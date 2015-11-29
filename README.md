[![Bower version](https://badge.fury.io/bo/firebase-auth-dialog.svg)](https://badge.fury.io/bo/firebase-auth-dialog)
[![Build Status](https://travis-ci.org/MeTaNoV/firebase-auth-dialog?branch=master)](https://travis-ci.org/MeTaNoV/firebase-auth-dialog)
[![Dependency Status](https://gemnasium.com/MeTaNoV/firebase-auth-dialog.svg)](https://gemnasium.com/MeTaNoV/firebase-auth-dialog)

## Demo

[https://metanov.github.io/firebase-auth-dialog/](https://metanov.github.io/firebase-auth-dialog/)

## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install firebase-auth-dialog --save
```

## Usage

Import Custom Element:

```html
<link rel="import" href="bower_components/firebase-auth-dialog/firebase-auth-dialog.html">
```

And then use it:

```html
	<firebase-auth-dialog id="firebaseAuthDialog"
		entry-animation="scale-up-animation"
		exit-animation="fade-out-animation"
		type="Register"
		location="https://metanov-test.firebaseio.com"
		providers='["facebook", "github", "google"]'
		modal with-backdrop>
	</firebase-auth-dialog>
```

See the [Documentation](https://metanov.github.io/firebase-auth-dialog/) for more options.

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

[MIT License](http://opensource.org/licenses/MIT) © Pascal Gula

[![Throughput Graph](https://graphs.waffle.io/MeTaNoV/firebase-auth-dialog/throughput.svg)](https://waffle.io/MeTaNoV/firebase-auth-dialog/metrics)

