# Sourcery Plugin for ArchivesSpace

A plug-in for ArchivesSpace which adds a page/resource action to request with Sourcery.

## Installation and Usage

To install the plugin, add the directly titled `sourcery` at the root of this repository to the `plugins` directory of your ArchivesSpace environment.

In your `config.rb` file: 

Add 'sourcery' to the plugins variable.
```ruby
AppConfig[:plugins] = ['sourcery']
```

If applicable, set your repository ID.  This is a Sourcery ID that can help populate your repository in the request creation screen. Your Sourcery contact should be able to provide this.
```ruby
AppConfig[:sourcery_repo_id] = 'your-repository-id'
```

To remove the default request button, disable the request page action variable.
```ruby
AppConfig[:pui_page_actions_request] = false
```

## Local Development/Testing

To point the request button to a development URL, you can set :sourcery_endpoint in your config.

```ruby
AppConfig[:sourcery_endpoint] = 'https://sourcery-dev.web.app'
```

## Development Overview

The following section briefly documents the key aspects of the plugin. For clarity, development to the main Sourcery app is included.

**public/plugin_init_rb**: Add's a Sourcery Button in the form of a page action to the following record types: `resource, archival_object, digital_object, digital_object_component`.

**public/views/shared/_sourcery_page_action.html.erb**: Sourcery button that creates a URL to Sourcery request creation to prepopulate fields.
