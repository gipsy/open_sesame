// Table of name prefixes

l-   |     layouts
m-   |     modules
is-  |     states (is-hidden, is-selected)

*** Example Sass ***
.l-single-centered-colum
  width: 400px
  margin: 0 auto

.m-box
  border: 1px solid black


*** Module components ***
Module components are child elements of modules.
They are always prefixed with the full name of the module they belong to followed by --, in order to:
  a) indicate their relationship, and
  b) prevent the component's styles from applying outside of the module's scope.


*** Example Sass ***
.m-box
  .m-box--header
    background-color: grey

  .m-box--body
    padding: 10px

*** Markup ***
<div class="m-box">
  <h1 class="m-box--header">Headline</h1>

  <div class="m-box--body">
    ... box content ...

    <!-- some other markup -->
      <!-- deep down in the box -->
        <!-- in some other context -->
          <div class="header" />
  </div>
</div>

Here we have a complete SMURF code example of both submodules and modifiers in action:

// -- module --
.m-box
  // components
  .m-box--header

  .m-box--body

  // modifiers
  &.no-border
    border: none

  &.right
    float: right

  // states
  &.is-disabled
    background-color: #ccc

// -- submodule --
.m-box_attention
  @extend .m-box
  border: 2px solid red

   // additional component, that only exists in the submodule
  .m-box_attention--teaser
HTML:

<div class="m-box_attention right is-disabled">

