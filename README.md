# Chosen for rails asset pipeline 

## Forked with Koenpunt's option adding (with custom callback)

Option adding

You can specify a create_option option, which can be a boolean or callback function.

Example for allowing adding of new items:

    $(function() {
      $(".chzn-select").chosen({
        create_option: true,
        // persistent_create_option decides if you can add any term, even if part
        // of the term is also found, or only unique, not overlapping terms
        persistent_create_option: true
      });
    });
Or with a callback and an AJAX request to, for example, save the terms in your database:

    $(function() {
      $(".chzn-select").chosen({
        create_option: function(term){
          var chosen = this;
          $.post('add_term.php', {term: term}, function(data){
            chosen.append_option({
              value: 'value-' + data.term,
              text: data.term
            });
          });
        }
      });
    });
Custom text

Through the options it is also possible to customize the text used in the 'Add option' link, like so:

    $(function() {
      $(".chzn-select").chosen({
        create_option_text: 'Create category'
      });
    });

## Normal README

[Chosen](https://github.com/harvesthq/chosen) is a library for making long, unwieldy select boxes more user friendly.

The `chosen-rails` gem integrates the `Chosen` with the Rails asset pipeline.

## Usage

### Install chosen-rails gem

Include `chosen-rails` in Gemefile

    gem 'chosen-rails'

Then run `bundle install`

### Include chosen javascript assets

Add to your `app/assets/javascripts/application.js` if use with jQuery

    //= require chosen-jquery

Or with Prototype

    //= require chosen-prototype

### Include chosen stylesheet assets

Add to your `app/assets/stylesheets/application.css`

    *= require chosen

## Gem maintenance

Maintain `chosen-rails` gem with `Rake` commands.

Update origin chosen source files.

    rake update-chosen

Publish gem.

    rake release

## License

use MIT license.
