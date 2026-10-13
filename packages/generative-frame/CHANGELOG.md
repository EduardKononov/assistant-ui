# generative-frame

## 0.0.6

### Patch Changes

- [#9543](https://github.com/assistant-ui/assistant-ui/pull/9543) [`b569bbd`](https://github.com/assistant-ui/assistant-ui/commit/b569bbd3c353b205acba6ef1ea17cb89575c76cf) - feat: `resolveSpec(spec, { state })` resolves a spec into the element tree the renderer draws for one state, with conditions, `repeat`, and expressions applied and action params resolved, for targets that cannot run a renderer. ([@okisdev](https://github.com/okisdev))

- [#9539](https://github.com/assistant-ui/assistant-ui/pull/9539) [`40b797d`](https://github.com/assistant-ui/assistant-ui/commit/40b797d9c2155e67b16261340f3d2be6b7d10e9a) - fix: an action list in a spec stops at the first action that fails, so a `setState` that confirms a host action runs only when that action succeeded. The failure is still reported to `onError`. ([@okisdev](https://github.com/okisdev))

- [#9548](https://github.com/assistant-ui/assistant-ui/pull/9548) [`1109afa`](https://github.com/assistant-ui/assistant-ui/commit/1109afabb2f9465ea93f152fb344fbd9da3ac125) - fix: a `render_spec` call that patches an earlier spec with the same title now renders on that spec when it mounts before its title has streamed in. The base follows the title, and the stream starts over when the title brings a new one. ([@okisdev](https://github.com/okisdev))

- [#9507](https://github.com/assistant-ui/assistant-ui/pull/9507) [`f9e5643`](https://github.com/assistant-ui/assistant-ui/commit/f9e56437a067df208216d9dd57cf421c5f2a5f21) - feat: the spec guidance now teaches how to compose an answer (the takeaway first, a `Card` for each module, key figures side by side, and a `Map`, `Timeline`, `Steps`, `Table`, or `Image` where the content calls for one), naming only the components a catalog has and only uses their slots and events allow, and no longer caps a spec at about 30 elements. `render_spec`'s description carries these rules and the app's `customRules`, and `createSpecTools` takes `customRules`, so the rules hold even when a model never loads the `spec` module. ([@okisdev](https://github.com/okisdev))

- [#9540](https://github.com/assistant-ui/assistant-ui/pull/9540) [`60cdf31`](https://github.com/assistant-ui/assistant-ui/commit/60cdf317a1da31983fc5bf69adbfa28eb63860a8) - feat: specs gain the built-in action `copyText` (`{ text }`), validated in every catalog, documented when `catalog.prompt({ hostApi: { clipboard: true } })` says the host handles it, and reserved in `defineCatalog`. The assistant-ui spec toolkits for the web and for Vue write it to the clipboard with `navigator.clipboard.writeText`, only from an event a component emits, never from `watch`, and a copy that does not happen fails, so an action after it in the list, such as a confirmation, does not run. The React Native build leaves it out of the guidance unless an app passes `handlers.copyText` and `specPrompt.hostApi.clipboard`. ([@okisdev](https://github.com/okisdev))

- [#9545](https://github.com/assistant-ui/assistant-ui/pull/9545) [`5402b93`](https://github.com/assistant-ui/assistant-ui/commit/5402b93a1e991d0a3e44e253d7bd67880931c835) - feat: `createSpecToolkit` from the new `generative-frame/spec/assistant-ui/vue` entry renders `render_spec` calls in an `@assistant-ui/vue` thread with Vue components, deriving the same thread state as the React toolkit: earlier calls with the same title, earlier tool results under `/tools` in frontend execution, saved state, and what a UI shares with the model. `@assistant-ui/vue` and `@assistant-ui/core` are optional peers of that entry. ([@okisdev](https://github.com/okisdev))

## 0.0.5

### Patch Changes

- [#9427](https://github.com/assistant-ui/assistant-ui/pull/9427) [`5113baa`](https://github.com/assistant-ui/assistant-ui/commit/5113baa64eb50e2b7be167323161bb173a19c610) - feat: with `render_spec` among the tools, `buildWidgetInstructions` and `useWidgetInstructions` tell the model when to answer in markdown, with a spec, or with a widget ([@okisdev](https://github.com/okisdev))

- [#9524](https://github.com/assistant-ui/assistant-ui/pull/9524) [`c5c4fdd`](https://github.com/assistant-ui/assistant-ui/commit/c5c4fddfb57aafc7ad3043d11fe1bb3cd773656b) - feat: a rendered UI can tell the model what the user chose. Specs gain the built-in actions `sendMessage` and `updateModelContext` (validated in every catalog, documented when `catalog.prompt({ hostApi })` says the host handles them, and reserved in `defineCatalog`), widget guidance documents `genframe.updateModelContext` behind `hostApi.modelContext`, and the assistant-ui toolkits handle both: what a UI shares goes into the system prompt of later requests, marked as data and capped at 4,000 characters, and is saved with the call's state so it survives a reload. `sendMessage` runs only from a user's event, never from `watch`, which action handlers can now tell apart through `kind` on their second argument. ([@okisdev](https://github.com/okisdev))

- [#9501](https://github.com/assistant-ui/assistant-ui/pull/9501) [`d30dae6`](https://github.com/assistant-ui/assistant-ui/commit/d30dae602477a50ace87710e27b06c3faf2a6e59) - feat: add `$calc` formulas to spec expressions, so a spec can compute totals, quantities that follow an input, and formatted values from its state. Formulas are parsed by a bounded interpreter (no `eval`), give `null` instead of throwing, and `validateSpec` reports one that does not parse as `invalid-formula`. The spec guidance and the format rules now describe them, and a pointer into an array reads only the array's own items. ([@okisdev](https://github.com/okisdev))

- [#9455](https://github.com/assistant-ui/assistant-ui/pull/9455) [`986d7cf`](https://github.com/assistant-ui/assistant-ui/commit/986d7cffa2e9cde3c262e5798de62e4b6618479c) - Require explicit `fontStyleOrigins` and `fontOrigins` options for external font providers such as Google Fonts. An empty CDN allowlist now blocks external stylesheets and font files unless their resource origins are configured. ([@Yonom](https://github.com/Yonom))

- [#9318](https://github.com/assistant-ui/assistant-ui/pull/9318) [`1de1657`](https://github.com/assistant-ui/assistant-ui/commit/1de16572935587752628401d7928ba7bf9932010) - feat: keep a widget's `genframe.setState` value across reloads in the assistant-ui toolkit, and seed a frame's state with `initialState` ([@okisdev](https://github.com/okisdev))

## 0.0.4

### Patch Changes

- [#9253](https://github.com/assistant-ui/assistant-ui/pull/9253) [`1a76908`](https://github.com/assistant-ui/assistant-ui/commit/1a76908402c56b9783f2a6b3eeff8081b94f3d78) - fix(generative-frame): pass an MCP Apps widget's `ui/initialize` params to a new `onInitialized` handler, including the display modes it declares ([@rupic-app](https://github.com/apps/rupic-app))

- [#9268](https://github.com/assistant-ui/assistant-ui/pull/9268) [`afb9ad2`](https://github.com/assistant-ui/assistant-ui/commit/afb9ad2d42e4178a51eadf1ef15ad9f25be9df57) - feat: add `unsafeShimDomain` to load the shim from a self-hosted domain, and `opaqueOrigin` in generative-frame to render widgets in a `null`-origin sandbox without a shim ([@Yonom](https://github.com/Yonom))

- [#9310](https://github.com/assistant-ui/assistant-ui/pull/9310) [`2b1e1f5`](https://github.com/assistant-ui/assistant-ui/commit/2b1e1f5f95cb4cca9a2d8001e1e3b1ac68e46a0f) - feat: render spec mode on React Native, where `generative-frame/spec/react` and `generative-frame/spec/assistant-ui` resolve to React Native builds through the `react-native` condition, with `react-native` and `@assistant-ui/react-native` as optional peers ([@okisdev](https://github.com/okisdev))

- [#9286](https://github.com/assistant-ui/assistant-ui/pull/9286) [`409b896`](https://github.com/assistant-ui/assistant-ui/commit/409b896bcc11d5b0420cd3bc83b5463046a43558) - fix: validate a patch-only `render_spec` call after a reload against the spec rendered from the thread ([@okisdev](https://github.com/okisdev))

- [#9296](https://github.com/assistant-ui/assistant-ui/pull/9296) [`984674e`](https://github.com/assistant-ui/assistant-ui/commit/984674e2e0ab454c166712900e2d225cc8bc1803) - feat: keep what the user changes in a rendered spec across reloads in the assistant-ui toolkit, on the web and on React Native, and let a spec state store list and restore its writes ([@okisdev](https://github.com/okisdev))

- [#9287](https://github.com/assistant-ui/assistant-ui/pull/9287) [`1881261`](https://github.com/assistant-ui/assistant-ui/commit/1881261fd5d6605cbd1256af4f7c3547d9075d48) - feat: let assistant-ui specs read earlier tool results from state expressions ([@okisdev](https://github.com/okisdev))

- [#9288](https://github.com/assistant-ui/assistant-ui/pull/9288) [`a151d03`](https://github.com/assistant-ui/assistant-ui/commit/a151d031ca07b9441dcccbc9ad2b3f05970a648b) - feat: add `generative-frame/spec/vue`, a Vue renderer for spec mode, with `vue` as an optional peer ([@okisdev](https://github.com/okisdev))
- Updated dependencies [[`afb9ad2`](https://github.com/assistant-ui/assistant-ui/commit/afb9ad2d42e4178a51eadf1ef15ad9f25be9df57)]:
  - safe-content-frame@0.0.34

## 0.0.3

### Patch Changes

- [#9223](https://github.com/assistant-ui/assistant-ui/pull/9223) [`52e6257`](https://github.com/assistant-ui/assistant-ui/commit/52e625796b7f1cfe20f23a854c471d761c4d95e6) - fix(generative-frame): accept Standard Schema optional result members with undefined ([@rupic-app](https://github.com/apps/rupic-app))

## 0.0.2

### Patch Changes

- [#9103](https://github.com/assistant-ui/assistant-ui/pull/9103) [`6dd864b`](https://github.com/assistant-ui/assistant-ui/commit/6dd864b23bcc9290abcc68eb6b097ab99495d136) - feat: stream model-generated HTML and SVG widgets into Safe Content Frames with an MCP Apps-compatible host bridge, theme tokens, diagnostics, in-frame screenshots, per-id persistent storage, provider-agnostic widget tools, prompt guidance, and a repair loop; React bindings and an assistant-ui toolkit; and a declarative spec mode in separate entry points (`generative-frame/spec`, `/spec/react`, `/spec/tools`, `/spec/assistant-ui`) that never bundles the frame ([@Yonom](https://github.com/Yonom))
