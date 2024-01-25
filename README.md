
# Rails Bootstrap Modal with TurboFrames Example

This Rails 7.1 project showcases the integration of a Bootstrap Modal (5.x.x) using TurboFrames, providing a dynamic and responsive user interface. The project is built using Ruby 3.2.2 and leverages the power of Hotwire's TurboFrames to update parts of the webpage without a full page reload.

You can finde the corresponding blog post for this project [here](https://michaelwapp.medium.com/integrating-bootstrap-5-modals-with-ruby-on-rails-7-using-turbo-frames-433a59751b33).

## Prerequisites

Before you begin, ensure you have the following installed:
- Ruby 3.2.2
- Rails 7.1
- Node.js and Yarn (for JavaScript dependencies)
- Bootstrap 5.3.x

## Getting Started

To get started with the project, clone the repository and install the necessary dependencies:

```bash
git clone https://your-repository-url.git
cd your-rails-project
bundle install
yarn install
```

## Running the Application

To run the application locally:

```bash
bin/dev
```

Navigate to `http://localhost:3000` in your web browser to view the application.

## Bootstrap Modal with TurboFrames

The application demonstrates how to use TurboFrames to dynamically load and display a Bootstrap modal. Here's an overview of the implementation:

### 1. Setup TurboFrames

Ensure that Turbo is included in your application. You can verify this in your `Gemfile` and `app/javascript/application.js`.

### 2. Create a Modal Partial

Create a partial view for the modal (e.g., `app/views/partials/_modal.html.erb`) and include the modal's HTML structure using Bootstrap classes.

### 3. Use TurboFrame to Load the Modal

Use a TurboFrame tag to wrap the area where the modal will be displayed. Set the `src` attribute to support propper form submission see [here](https://turbo.hotwired.dev/reference/frames#frame-that-drives-navigation-to-replace-whole-page).

Example:

```erb
# app/views/layout/application.html.erb
<%= turbo_frame_tag "modal", src: "_top" %>
```

### 4. Triggering the Modal

Use a link or a button to trigger the modal. The link should target the TurboFrame ID to load the modal content without a full page reload.

Example:

```erb
<%= link_to "Open Modal", modal_path, data: { turbo: true, turbo_frame: "modal" } %>
```

### 5. Using the Modal for a Controller Action

In order to use the modal as a response to a controller action rendering the partial can be done like this: 

Example for the `new` action:

```ruby
<%= render 'partials/modal', title: "New Project", fade_in: true do %>
  <%= render "form", project: @project %>
<% end %>
```

As the modal partial includes the turbo_frame definition, it automatically only updates the turbo_frame by rendering the modal. 

## Further Information

For more information on TurboFrames and Bootstrap, refer to the following resources:
- [Hotwire Turbo](https://turbo.hotwired.dev/)
- [Bootstrap Documentation](https://getbootstrap.com/docs/)

### Contact

For more details, contact [me](michaelwapp.com)

Copyright Michael Bauer-Wapp 2024
