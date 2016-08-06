# nanomorph [![stability][0]][1]
[![npm version][2]][3] [![build status][4]][5] [![test coverage][6]][7]
[![downloads][8]][9] [![js-standard-style][10]][11]

Hyper fast diffing algorithm for real DOM nodes :zap:
## Usage
```js
const nanomorph = require('nanomorph')
const bel = require('bel')

var tree = null

var el1 = bel`<div>hello people</div>`
var el2 = bel`<div>nanananana-na-no</div>`
var el2 = bel`<div>teeny, tiny, tin bottle</div>`

update(el1)
update(el2)
update(el3)

function update (el) {
  if (!tree) {
    tree = el
    document.body.appendChild(tree)
  } else {
    tree = nanomorph(el, tree)
  }
}
```

## API
### tree = nanomorph(newTree, oldTree)
Diff a tree of HTML elements against another tree of HTML elements and create
a patched result that can be applied on the DOM.

## FAQ
### Why are you building this?
Experimentin' is fun - all this is is a take on seeing how small we can get
with real DOM node diffing. And if we can make some good heuristics happen for
efficient tree updates ([Merkle trees][mt], anyone?) that'd be nice.

### Should I use this right now?
No, probably not but if you do it'll probably be the fastest thing ever.
Seriously, I doubt this could be made a lot faster than it is right now, unless
we're talking edge cases. But yeah, alright go ahead if you like.

## Installation
```sh
$ npm install nanomorph
```

## See Also
- [morphdom][morphdom]
- [yo-yo][yo-yo]
- [virtual-raf](https://github.com/yoshuawuyts/virtual-raf)
- [how to write your own virtual dom 1][own-vdom-1]
- [how to write your own virtual dom 2][own-vdom-2]

## License
[MIT](https://tldrlegal.com/license/mit-license)

[own-vdom-1]: https://medium.com/@deathmood/how-to-write-your-own-virtual-dom-ee74acc13060
[own-vdom-2]: https://medium.com/@deathmood/write-your-virtual-dom-2-props-events-a957608f5c76

[0]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/nanomorph.svg?style=flat-square
[3]: https://npmjs.org/package/nanomorph
[4]: https://img.shields.io/travis/yoshuawuyts/nanomorph/master.svg?style=flat-square
[5]: https://travis-ci.org/yoshuawuyts/nanomorph
[6]: https://img.shields.io/codecov/c/github/yoshuawuyts/nanomorph/master.svg?style=flat-square
[7]: https://codecov.io/github/yoshuawuyts/nanomorph
[8]: http://img.shields.io/npm/dm/nanomorph.svg?style=flat-square
[9]: https://npmjs.org/package/nanomorph
[10]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[11]: https://github.com/feross/standard
[morphdom]: https://github.com/patrick-steele-idem/morphdom
[yo-yo]: https://github.com/maxogden/yo-yo
[mt]: https://en.wikipedia.org/wiki/Merkle_tree
