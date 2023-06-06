# Sourcery Plugin for Archive Space

A plug-in for ArchiveSpace which replaces the default request workflow with Sourcery.

## Installation and Usage

To install the plugin, add the directly titled `sourcery` at the root of this repository to the `plugins` directory of your ArchiveSpace environment.

In `common/config/config.rb`: 

Add 'sourcery' to the plugins variable.
```ruby
AppConfig[:plugins] = ['sourcery']
```
If applicable, set your organization id.  Your Sourcery contact should be able to provide this.
```ruby
AppConfig[:sourcery_org_id] = 'your-org-id'
```

To remove the default request button, disable the request page action variable.
```ruby
AppConfig[:pui_page_actions_request] = false
```

## Local Development/Testing

To point the request button to a development URL, you can set :sourcery_endpoint in your config.

```ruby
AppConfig[:sourcery_endpoint] = 'https://devurl.web.app'
```

## Technical Overview

The following section briefly documents the key aspects of the workflow and implementation. For clarity, development to the main Sourcery app is included.

### ArchiveSpace 

**public/plugin_init_rb**: Add's a Sourcery Button in the form of a page action to the following record types: `resource, archival_object, digital_object, digital_object_component`.

**public/views/shared/_sourcery_page_action.html.erb**: Sourcery Button opens a link to sourceryapp.org/archivespace. The following record descriptors are passed as parameters through the url: organization id, record uri, citation, display string, and repository. 

