[![Bower version](https://badge.fury.io/bo/firebase-element-extended.svg)](https://badge.fury.io/bo/firebase-element-extended)
[![Build Status](https://travis-ci.org/MeTaNoV/firebase-element-extended.svg?branch=master)](https://travis-ci.org/MeTaNoV/firebase-element-extended)
[![Dependency Status](https://gemnasium.com/MeTaNoV/firebase-element-extended.svg)](https://gemnasium.com/MeTaNoV/firebase-element-extended)

## Demo

[https://metanov.github.io/firebase-element-extended/](https://metanov.github.io/firebase-element-extended/)

## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install firebase-element-extended --save
```

## Usage

Import one of the element of the set with the following:

```html
<link rel="import" href="bower_components/firebase-element-extended/firebase-auth-dialog.html">
```

The first component available is `<firebase-auth-dialog>`

To use it:

```html
<firebase-auth-dialog
	entry-animation="scale-up-animation"
	exit-animation="fade-out-animation"
	type="Register"
	providers='["facebook", "github", "google"]'
	modal with-backdrop>
    <span introduction>-- Welcome to the Firebase Element eXtended Demo: --</span>
    <span provider>-- Register with one of the following provider(s): --</span>
    <span user>-- or provide an email and password for registration : --</span>
</firebase-auth-dialog>
```

See the [Documentation](https://metanov.github.io/firebase-element-extended/) for more options.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

[MIT License](http://opensource.org/licenses/MIT) © Pascal Gula

[![Throughput Graph](https://graphs.waffle.io/MeTaNoV/firebase-element-extended/throughput.svg)](https://waffle.io/MeTaNoV/firebase-element-extended/metrics)

