---
published: true
title: System Test dan Integration Test pada Rails
layout: post
categories: ruby
tags: [ruby, testing]
---

**1. System test digunakan untuk menguji interaksi pengguna** dengan aplikasi Rails menggunakan _real atau headless browsers_. 
Tes ini membutuhkan Capybara. Contoh:

```ruby
RSpec.describe "Todos", type: :system do
  it "create a todo" do
    visit root_path
    
    click_on "Create a new todo"
    fill_in "Title", with: "first title"
    click_on "Create Todo"  

    expect(page).to have_css("ul.todos.incomplete li", text: "first title")
    
  end
end
```

Jadi System test ini cenderung mengetes aplikasi dari sudut pandang pengguna. 
Pada Rspec versi 3.7 kebawah, tes ini mirip dengan Feature spec.

**2. Integration test digunakan untuk menguji bagaimana berbagai bagian aplikasi Rails berinteraksi.**
Umumnya digunakan untuk menguji alur kerja penting dalam aplikasi kita. 
Test ini mempunyai _HTTP request method seperti: “get”, “put”, “post”, dll._ sedangkan system test tidak. contoh:

```ruby
RSpec.describe "Widget management", :type => :request do

  it "creates a Widget and redirects to the Widget's page" do
    get "/widgets/new"
    expect(response).to render_template(:new)

    post "/widgets", :widget => {:name => "My Widget"}

    expect(response).to redirect_to(assigns(:widget))
    follow_redirect!

    expect(response).to render_template(:show)
    expect(response.body).to include("Widget was successfully created.")
  end

  it "does not render a different template" do
    get "/widgets/new"
    expect(response).to_not render_template(:show)
  end
end
```
Pada Rspec, tes ini mirip dengan Request spec, karena memang Request spec adalah _wrapper_ dari Integration test pada Rails.

Referensi:
- https://guides.rubyonrails.org/testing.html
- https://relishapp.com/rspec/rspec-rails/v/3-8/docs/feature-specs/feature-spec
- https://relishapp.com/rspec/rspec-rails/v/3-8/docs/request-specs/request-spec