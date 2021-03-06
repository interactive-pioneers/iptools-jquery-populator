# iptools-jquery-populator [![Build Status](http://img.shields.io/travis/interactive-pioneers/iptools-jquery-populator.svg)](https://travis-ci.org/interactive-pioneers/iptools-jquery-populator) [![Bower version](https://badge.fury.io/bo/iptools-jquery-populator.svg)](http://badge.fury.io/bo/iptools-jquery-populator)

jQuery plugin that populates form control value(s) to other control(s).

## Installation

```
bower install iptools-jquery-populator
```

## Features

- Populate values automatically from one form control to the other on its `change` or `blur` events based on `data-population-target` attribute
- Populate values manually from one form control to the other with `populateManual()` method call based on `data-population-target-manual` attribute
- Listen to population to retrieve event `type`, `source` and `target` controls of the population
- Populate single value to multiple targets

## Options

All options are delivered over data attributes on form controls which values should be populated to other control(s).

| Option | Description |
| ------ | ----------- |
| `data-population-target` | Single or comma-separated list of selectors for form controls receiving data on `change` or `blur` events |
| `data-population-target-manual` | Single or comma-separated list of selectors for form controls receiving data on `populateManual()` method call |

## Events

Events are dispatched on element that populator was initialised on, e.g. `<form>`.

| Event | Description |
| ------ | ----------- |
| `success` | Dispatched whenever value was populated successfully. |
| `error` | Dispatched whenever values was popuplated erroneously. |

Event structure:

```js
{
  type: '<event type>', // populationMismatch or populationSuccess
  target: '<jQuery Object>', // target element receiving populated value
  source: '<jQuery Object>', // source element defining populated
}
```

## Requirements

- jQuery 1.3.2 or greater

## Example

```html
<form action="/billing" method="post">
  <input type="text" data-population-target="#js_shipping_name" name="billing_name" value="Interactive Pioneers GmbH">
</form>

<form action="/shipping" method="post">
  <input type="text" name="shipping_name" id="js_shipping_name">
</form>

<script>
jQuery(document).ready(function($) {
  $('form:first').iptPopulator();
});
</script>
```

## Contributions

### Bug reports, suggestions

- File all your issues, feature requests [here](https://github.com/interactive-pioneers/iptools-jquery-populator/issues)
- If filing a bug report, follow the convention of _Steps to reproduce_ / _What happens?_ / _What should happen?_
- __If you're a developer, write a failing test instead of a bug report__ and send a Pull Request

### Code

1. Fork it ( https://github.com/[my-github-username]/iptools-jquery-populator/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Develop your feature by concepts of [TDD](http://en.wikipedia.org/wiki/Test-driven_development), see [Tips](#tips)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request

### Tips

Following tasks are there to help with development:

- `grunt watch:bdd` listens to tests and source, reruns tests
- `grunt qa` run QA task that includes tests and JSHint
- `grunt build` minify source to dist/

## Licence
Copyright © 2015 Interactive Pioneers GmbH. Licenced under [GPLv3](LICENSE).
