---
title: list
label: List
---
The list widget allows you to create a repeatable item in the UI which saves as a list of widget values. map a user-provided string with a comma delimiter into a list. You can choose any widget as a child of a list widget—even other lists.

* **Name:** `list`
* **UI:** without any `fields` specified, the list widget defaults to a text input for entering comma-separated values; with `fields`  specified, the list widget contains a repeatable child widget, with controls for adding, deleting, and re-ordering the repeated widgets.
* **Data type:** list of widget values
* **Options:**

  * `default`: you may specify a list of strings to populate the basic text field, but declare defaults on the child widgets if you are specifying `fields`;
  * `allow_add`: `false` hides the button to add additional items
  * `collapsed`: when `true`, the entries collapse by default
  * `summary`: specify the label displayed on collapsed entries
  * `minimize_collapsed`: when `true`, collapsing the list widget will hide all of it's entries instead of showing summaries
  * `label_singular`: the text to show on the add button
  * `field`: a single widget field to be repeated
  * `fields`: a nested list of multiple widget fields to be included in each repeatable iteration
* **Example** (`field`/`fields` not specified):

  ```yaml
  - label: "Tags"
    name: "tags"
    widget: "list"
    default: ["news"]
  ```
* **Example** (`allow_add` marked `false`):

  ```yaml
  - label: "Tags"
    name: "tags"
    widget: "list"
    allow_add: false
    default: ["news"]
  ```
* **Example** (with `field`):

  ```yaml
  - label: "Gallery"
    name: "galleryImages"
    widget: "list"
    summary: '{{fields.image}}'
    field: {label: Image, name: image, widget: image}
  ```
* **Example** (with `fields`):

  ```yaml
  - label: "Testimonials"
    name: "testimonials"
    widget: "list"
    summary: '{{fields.quote}} - {{fields.author.name}}'
    fields:
      - {label: Quote, name: quote, widget: string, default: "Everything is awesome!"}
      - label: Author
        name: author
        widget: object
        fields:
          - {label: Name, name: name, widget: string, default: "Emmet"}
          - {label: Avatar, name: avatar, widget: image, default: "/img/emmet.jpg"}
  ```
* **Example** (`collapsed` marked `false`):

  ```yaml
  - label: "Testimonials"
    name: "testimonials"
    collapsed: false
    widget: "list"
    fields:
      - {label: Quote, name: quote, widget: string, default: "Everything is awesome!"}
      - {label: Author, name: author, widget: string }
  ```
* **Example** (`minimize_collapsed` marked `true`):

  ```yaml
  - label: "Testimonials"
    name: "testimonials"
    minimize_collapsed: true
    widget: "list"
    fields:
      - {label: Quote, name: quote, widget: string, default: "Everything is awesome!"}
      - {label: Author, name: author, widget: string }
  ```