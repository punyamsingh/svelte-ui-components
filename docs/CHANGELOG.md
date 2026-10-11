# Changelog All notable changes to this project will be documented in this file. The format is
based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/juspay/svelte-ui-components/compare/HEAD..4.54.2)

## [4.54.2](https://github.com/juspay/svelte-ui-components/compare/4.54.2..4.53.1) - 11 October 2026

A column header clamped to a canvas edge was inset 2px from it, but its
label plate is drawn 3px beyond the text, so the plate hung 0.71px outside
the svg and was clipped there. The right edge had the same 1px twin
whenever the right clamp bound.

Inset the clamp by the plate padding, now a shared constant so the two
cannot drift again, and add a fixture that makes each clamp bind plus a
spec asserting every header plate lies inside the svg. The fixture keeps the
cases out of the docs demo, so its visual baseline does not move.

-
fix(date-range-picker): let compareCalendar reach the compare draft so Apply and Cancel work ([3d6b629](https://github.com/punyamsingh/svelte-ui-components/commit/3d6b629871b682cd851b2fa8936d8dbd7a8a1b0d))
-
fix(sankey): keep header label plates inside the chart svg ([e4a38d6](https://github.com/punyamsingh/svelte-ui-components/commit/e4a38d6dc1ed1ea0e7d1097701bc27a6c6d706cd))
-
fix(scroll-lock): restore an owner's inline style verbatim and tolerate sealed owners ([496939a](https://github.com/punyamsingh/svelte-ui-components/commit/496939a27003c593da9bc693b9e30726b763f30a))
-
docs(audit): correct docs and comments that no longer match release 4.53.0 ([4919eb8](https://github.com/punyamsingh/svelte-ui-components/commit/4919eb80776ae17600d8ce1ea9bf92c884600007))
-
fix(package): keep the theme CSS import when a bundler drops side-effect-free modules ([85c6dd0](https://github.com/punyamsingh/svelte-ui-components/commit/85c6dd0b1d2310b0f8bec80b180ed3f90a08e669))
-
feat(chatcomposer): open the command menu on each command's own trigger character ([45c6bbe](https://github.com/punyamsingh/svelte-ui-components/commit/45c6bbea4a8978f48785b4f9ea02d90e45688424))
-
fix: bridge remaining content slots and reject scroll lookalikes ([f5db457](https://github.com/punyamsingh/svelte-ui-components/commit/f5db45783ad8773aa1832022fd25692bc5baaa0b))
-
ci(browser-engines): pause the weekly run until its first run is green ([91c2880](https://github.com/punyamsingh/svelte-ui-components/commit/91c288077fe509ddf16ca6687cc377b69be58894))

## [4.53.1](https://github.com/juspay/svelte-ui-components/compare/4.53.1..2.91.2) - 10 October 2026

Brings the audit work that never reached release onto d3610f2: the local candidate 2c9e94c,
merged three-way from its 4e073fd parent. The HITL expiry, Toast lifecycle, compiled chart
label and Select placement changes that merged in the meantime are kept as they are.

Behavior:
- Pill and Tabs semantics, with independent native primary and dismiss buttons where a pill is
both actionable and dismissible.
- Form-associated controls: required, first-invalid, name, value, fieldset and cross-document
adoption behavior, in the Svelte components and the custom elements.
- Contextual names, headings and landmarks across Chat, Book, Pagination, Table, Modal,
MediaPlayer and the attachment strip. MediaPlayer's video surface is now a native button
instead of a video carrying role="button".
- Tabs RTL, fit, font, zero-axis and scale behavior, and scrolling for keyboard, chat,
Markdown tables and Table.
- Shared public-API and custom-element scroll locks across separately built bundles and
adopted elements.

New optional props: ariaLabel (AttachmentChipRow, Book, ChatMessageList, MediaPlayer,
Pagination), Chat messageListLabel, markdownTableLabel, and Table label members
selectionColumn, rowAction and pageNavigation. No existing prop default changes in the
components, and Table's rowsPerPage label keeps its released text.

Consumer-facing text and examples:
- The example pages for the touched components (60 route files) now carry real headings and
the new names, and show suppressRoleAndTabindex where a nested item must not be a button.
- The install-time notice and the codemod --help text no longer announce changes "coming in
4.0.0" at 4.52; they describe the current migration guidance and the same codemod command.

Tests and tooling:
- The overlay specs keep the pointer and keyboard activations and the full inline-declaration
oracle, and add real Tab traversal and host edits made while a lock is held.
- Hover-label cases for the Table sort and ChatComposer attach buttons, in light and dark.
- Durable narration observer for the chart narration tests.
- scripts/check-focus-visible.js: the Select search-field note and line reference follow the
current suppression.
- .github/workflows/browser-engines.yml runs the functional and walkthrough suites in Firefox
and WebKit weekly, with no retries.
- docs/Resizable.md notes that arrow-key direction became edge-aware in 4.37.0, and the
Windows junction comment in scripts/link-local-peers.mjs no longer claims no elevation.

Refs #651, #679, #681

-
**BREAKING:** feat(events)!: remove the 3.x legacy spellings and host-reserved element props ([190800b](https://github.com/punyamsingh/svelte-ui-components/commit/190800b1e485af878b7af5639752c0d48e4edaef))
-
**BREAKING:** fix(release): derive both packages' versions from every unreleased commit ([a9f2e1c](https://github.com/punyamsingh/svelte-ui-components/commit/a9f2e1c106d4989dc0f7c277fe926e89f552ca2b))
-
**BREAKING:** feat(toolbar)!: render the default back control as a button with an inline icon ([83c406d](https://github.com/punyamsingh/svelte-ui-components/commit/83c406d81dd20432927b1cf728eed4fb2a7fe88c))
-
**BREAKING:** docs(release)!: record that the 3.x removal shipped in 3.5.1, and cut it as 4.0.0 ([3013d88](https://github.com/punyamsingh/svelte-ui-components/commit/3013d8858ae7a07fa96b6dea172f60f7b2fddb81))
-
feat: component capability and accessibility pass, and the defects it surfaced ([8ff28c1](https://github.com/punyamsingh/svelte-ui-components/commit/8ff28c102d209addaeee75a5965d993cca73c7e9))
-
feat(a11y): resolve the component-library audit and add the props it needed ([f127358](https://github.com/punyamsingh/svelte-ui-components/commit/f12735889acf858f485b3c9e16a054ad2cc5960d))
-
feat(events): make every event prop lowercase, keeping the old spellings as aliases ([9814b53](https://github.com/punyamsingh/svelte-ui-components/commit/9814b532e8489a5d969ca0ddb44e7bf14d0627c2))
-
feat(a11y): close the remaining audit defects in forms, tabs, overlays and naming ([0a8701d](https://github.com/punyamsingh/svelte-ui-components/commit/0a8701de8590f4b0b15e7225e428269a10875f2a))
-
feat(components): add the hooks and primitives apps were rebuilding locally ([fdee407](https://github.com/punyamsingh/svelte-ui-components/commit/fdee4071fdfe50dfa9c5f68d6502b532d4c6ffb9))
-
feat(components): the APIs Lighthouse's component-reuse audit found missing ([1786266](https://github.com/punyamsingh/svelte-ui-components/commit/17862661ef8e36150210f4173dfbd98b9bef3e76))
-
feat: add chat components ([a18c497](https://github.com/punyamsingh/svelte-ui-components/commit/a18c4976aa885efd2c006dff7ca06fedd2c9f537))
-
fix(changelog): render every release's commits and summary, starting with 3.2.0 ([41b1330](https://github.com/punyamsingh/svelte-ui-components/commit/41b1330be1ad771f5bbf47ee36ef0e906af1bc3a))
-
feat(chat): ship the agent-chat UX pack — trace-capable ThinkingIndicator, ToolCallLog, TaskList, SoundKit ([dc5d719](https://github.com/punyamsingh/svelte-ui-components/commit/dc5d71947d72e0bf710f40c38fc6ca7e3794e178))
-
docs: correct prop and CSS-variable tables across 44 component docs ([0b80c88](https://github.com/punyamsingh/svelte-ui-components/commit/0b80c887062e4f7e58589cd5bdfa7ed1ef0286a4))
-
feat(migrate): consumer migration for the seven breaking changes in this release ([d0e9462](https://github.com/punyamsingh/svelte-ui-components/commit/d0e9462021620a43ba0547115505cd0dd2313c5c))
-
feat: add four chat primitives — ThinkingIndicator, TypewriterText, AttachmentChipRow, HITL ([aa5f30a](https://github.com/punyamsingh/svelte-ui-components/commit/aa5f30ab8efff95bbebd73d8318f853f9455e142))
-
feat(motion): unified motion token system, tokenized overlay transitions ([13cd979](https://github.com/punyamsingh/svelte-ui-components/commit/13cd979ba3be1d1df4324f9e7402691a62bf1b7d))
-
fix(migrate): unblock the release and ship the migration to consumers ([56b9f08](https://github.com/punyamsingh/svelte-ui-components/commit/56b9f08a06bf3b96590e6745330d68c983c6f8ed))
-
feat(date-range-picker): add presetsPosition and an opt-in responsiveLayout ([eb1b92d](https://github.com/punyamsingh/svelte-ui-components/commit/eb1b92deaf991db503fdf50b33582ca4221cb150))
-
fix(migrate): close the gaps an adversarial pass found in this tooling ([ea00e98](https://github.com/punyamsingh/svelte-ui-components/commit/ea00e98502a3b52d1f0b199ae96f3ec46defc80e))
-
fix(tests): wait for hydration before driving demo pages ([b1a6ca6](https://github.com/punyamsingh/svelte-ui-components/commit/b1a6ca6f350fb8b29ea6956aa39ccec0879b93b9))
-
feat(wc): expose every component prop on its custom element, and register three ([97576f4](https://github.com/punyamsingh/svelte-ui-components/commit/97576f4260b4ce3d976482b6d22b04c99ec2e73a))
-
feat(codemod): add polymorph consumer migration codemod ([a9939e6](https://github.com/punyamsingh/svelte-ui-components/commit/a9939e6244051f85c3649cd0e7232ae27c8401fa))
-
fix(overlays): support owned scroll containers across modal surfaces ([5b95c2a](https://github.com/punyamsingh/svelte-ui-components/commit/5b95c2a789ee8c69a04b2d9fb6325ff34fb12847))
-
feat(speech): add SpeechSynthesisController ([2feb881](https://github.com/punyamsingh/svelte-ui-components/commit/2feb881309ed7770a3d1c47efbea3f769754ed57))
-
feat(button): add a shrinkable prop so a label can truncate inside a constrained parent ([4791ac0](https://github.com/punyamsingh/svelte-ui-components/commit/4791ac08ffe6af0065162752db459740b8ead98a))
-
fix(charts): honour the non-finite input policy in the five charts that never implemented it ([c2995d0](https://github.com/punyamsingh/svelte-ui-components/commit/c2995d065b1775d0a5b8534d76bbefed818e3f97))
-
feat(events): accept the corrected spelling for every event prop ([0f53508](https://github.com/punyamsingh/svelte-ui-components/commit/0f535083ad74c0e71da4f2d1318c04bc058d38b2))
-
feat(charts): show optional per-series aggregates in legends ([1b23707](https://github.com/punyamsingh/svelte-ui-components/commit/1b237070dda70ae00194b12267dcdfbb0777c030))
-
feat(a11y): keyboard and ARIA coverage for eight components, and the gaps it found ([93d22cb](https://github.com/punyamsingh/svelte-ui-components/commit/93d22cb4c84217f0cc7c42a95af160eae99f54c9))
-
feat(MarkdownText,ChatMessage): add sanitized markdown rendering ([be6fd57](https://github.com/punyamsingh/svelte-ui-components/commit/be6fd57f60170c6d27ffe814288bbdd294a13cb4))
-
feat: add DockPanel and pill composer variant ([2e08d6a](https://github.com/punyamsingh/svelte-ui-components/commit/2e08d6a6898efbca3f09630e856c1ea98fa7fc23))
-
feat: add automatic assistant shell prerequisites ([5241b87](https://github.com/punyamsingh/svelte-ui-components/commit/5241b87ecf8bd27c8ea9ec52719cdd56d5c09357))
-
feat(modal): clamp every size to the viewport and let footer actions wrap ([ba46fc8](https://github.com/punyamsingh/svelte-ui-components/commit/ba46fc86b3a182926d9b8be3932ebb4d946d56e6))
-
fix(wc): declare the corrected event spellings on every custom-element wrapper ([f952bfe](https://github.com/punyamsingh/svelte-ui-components/commit/f952bfe7e28734c7495a62c76004df1023bb1b6d))
-
feat(animated-number): add an entry animation, and keep a literal space from collapsing ([8339db8](https://github.com/punyamsingh/svelte-ui-components/commit/8339db8888b69f917094bf3f77b17680ec95f0c9))
-
feat(select): add an in-menu search placement ([e6236d0](https://github.com/punyamsingh/svelte-ui-components/commit/e6236d0a4eefb60fc7de5cb8113283ac06d2db45))
-
feat(select): add error state, trigger clear button and pressed feedback ([50835c2](https://github.com/punyamsingh/svelte-ui-components/commit/50835c2e48843fe7764ab82de7449e94fe9e2576))
-
feat(media-player): add a seek bar, an elapsed/total clock and a fullscreen toggle ([962f218](https://github.com/punyamsingh/svelte-ui-components/commit/962f2181da60ca1e8858066d510526f6b0e42ae1))
-
feat(components): keep Pill dismissal legible and label Toggle inputs ([5b453b7](https://github.com/punyamsingh/svelte-ui-components/commit/5b453b70ec41e8f39d96fb898567d725117cf7fa))
-
feat(charts): add createNarrationHighlighter for the onChartReady hook ([ef41824](https://github.com/punyamsingh/svelte-ui-components/commit/ef418243aaf7e6dabde0b90e72fd0727b1d10055))
-
feat(snippet): extract the copy affordance as createCopyState ([756408b](https://github.com/punyamsingh/svelte-ui-components/commit/756408bf5bc5d24d268de00f919add59e42aaf14))
-
feat(select): anchor the dropdown to a corner, so it can open upward ([0102628](https://github.com/punyamsingh/svelte-ui-components/commit/0102628c0dab4e1a38081e8964271a8125f69481))
-
feat(checkbox,toggle,select): participate in native form submission ([6c6dbec](https://github.com/punyamsingh/svelte-ui-components/commit/6c6dbece7b8168d07216cc0f6cb81648aca04e62))
-
feat: add SpeechToTextController — a headless speech-to-text engine for chat composers ([e34dbb4](https://github.com/punyamsingh/svelte-ui-components/commit/e34dbb49cf4d8277ceeeb5b11a67194b9d31cfac))
-
feat(migrate): add consumer migration script for the 3.x upgrade ([a453ea7](https://github.com/punyamsingh/svelte-ui-components/commit/a453ea770cebffc06b6d31b7239df3745a36f095))
-
feat(pie-chart): add a right-side value legend with a capped +N more expander ([5c9f40b](https://github.com/punyamsingh/svelte-ui-components/commit/5c9f40ba3291df4239a4e5da3a11e0f89ef3f7d0))
-
feat(migrate): consumer migration script, casing rename map, and checker fix ([48281df](https://github.com/punyamsingh/svelte-ui-components/commit/48281df1fa5908a6dbf4dfc80908d9d827b5f294))
-
fix(review): resolve the findings left open on merged PRs ([78883b5](https://github.com/punyamsingh/svelte-ui-components/commit/78883b54367b7db047226fe6674f1c2089809db8))
-
test(visual): add container-pinned visual regression suite for the demo routes ([6e28399](https://github.com/punyamsingh/svelte-ui-components/commit/6e2839941280ebd91c07cb753424c6033908223a))
-
feat(card,pill): deprecate the attrs keys each component overwrites ([cfaa899](https://github.com/punyamsingh/svelte-ui-components/commit/cfaa899c934ff1d963b802563bafcbbc9b2a7990))
-
feat(list-item): add tokens to stack the top row and let its cells shrink ([d686839](https://github.com/punyamsingh/svelte-ui-components/commit/d686839d8053543ac656ebbbf2db5af4a6f87280))
-
feat(markdown-text): render raw HTML through a sanitizer the caller supplies ([3997114](https://github.com/punyamsingh/svelte-ui-components/commit/3997114e08112d1e0291f5d35abc78176d7a342a))
-
feat(chatcomposer): support async boolean onsubmit and per-control disable ([6806370](https://github.com/punyamsingh/svelte-ui-components/commit/6806370e43c61568e58981ae3e5f65796b8f0011))
-
feat: messageBody snippet and a pin-sender-turn scroll policy for host chat adoptions ([529f1f0](https://github.com/punyamsingh/svelte-ui-components/commit/529f1f0af278f72dc6a8776ddd9daf7ed6fee105))
-
fix(codemod): lint scripts and tests, and parse module specifiers ([96f8e9f](https://github.com/punyamsingh/svelte-ui-components/commit/96f8e9fc401b32fa845e8f82775415ac17e81105))
-
docs(parity): remove the Bits UI comparison documents ([8a2848f](https://github.com/punyamsingh/svelte-ui-components/commit/8a2848f9b6a45255661a7e3215d6edab5f741345))
-
fix: emit a native testID alongside data-pw for every testId ([b543c3c](https://github.com/punyamsingh/svelte-ui-components/commit/b543c3c7f6d89f3e7dc4e2cfa09bcf93d17918fb))
-
feat(markdowntext): add a sanitize prop with protocol and tag allow-lists ([17f0f4d](https://github.com/punyamsingh/svelte-ui-components/commit/17f0f4dbc6d89ebfd1e1ec93f38748b777ddbe3d))
-
feat(sheet): let top/bottom panels be width-capped and centred ([21f3975](https://github.com/punyamsingh/svelte-ui-components/commit/21f397587c36a46d08089d9dc829212e55a10367))
-
feat(Input, Button, Menu): finish the capability gaps the first pass left open ([1aec3c4](https://github.com/punyamsingh/svelte-ui-components/commit/1aec3c45ba6e6ecf4421639aba1db3ba588df3c9))
-
fix(Img): sanitize fetched SVG before adoption; expose show-indicator on sui-choicebox ([0d2f92d](https://github.com/punyamsingh/svelte-ui-components/commit/0d2f92d9930a5bb2b50c22583100062bebeea6ff))
-
feat(modal): accessible name, ARIA dialog semantics, a real focus trap and a unified ondismiss ([ee69c9d](https://github.com/punyamsingh/svelte-ui-components/commit/ee69c9dbf3bdd34ffd14e9ed55270f42dd10df08))
-
fix(Select): add usePortal so the dropdown escapes overflow-clipping ancestors ([f649f2b](https://github.com/punyamsingh/svelte-ui-components/commit/f649f2bdb71e172a7d182ede25fff4e124b01196))
-
feat(wc): expose ChipInput, ColorPicker, Combobox and SplitInput as custom elements ([ff24661](https://github.com/punyamsingh/svelte-ui-components/commit/ff24661d61290dde69f7d34399ced12e7c4d63ba))
-
feat(pill): render a real button root for interactive chips ([a581f1e](https://github.com/punyamsingh/svelte-ui-components/commit/a581f1e5a2b0ddeb2340ca24318d695049e4c58e))
-
feat(ChatMessage): reveal a streamed message progressively via TypewriterText ([e96ec81](https://github.com/punyamsingh/svelte-ui-components/commit/e96ec8122dd3769bc807d1f1990b0ca30a95b805))
-
feat(markdown-text): let sanitize strip raw HTML instead of escaping it ([c242972](https://github.com/punyamsingh/svelte-ui-components/commit/c2429727b55e0e4fc9777d488ad952c9f2f053d7))
-
feat(Table): render row selection with the library Checkbox ([a2d2a70](https://github.com/punyamsingh/svelte-ui-components/commit/a2d2a70efe8e260f3bbc55b8adc68a5e1bb2849d))
-
feat(Input, Menu, Button): close the capability gaps forcing hand-rolled controls ([1e9e278](https://github.com/punyamsingh/svelte-ui-components/commit/1e9e2780e8eeccbe643c0d91477fc62a7dff8aec))
-
fix(sheet): name the dismissible overlay and restore the panel's focus ring ([6162f5f](https://github.com/punyamsingh/svelte-ui-components/commit/6162f5f1fa661be1b08e4baf294f56bc2f5cf86f))
-
feat(ThinkingIndicator): add chip variant, retire ChatToolStatus internally ([0c9a9b3](https://github.com/punyamsingh/svelte-ui-components/commit/0c9a9b39ff0d5f3ba3cbf8b657eb0adab38a318e))
-
feat(ChatMessage): collapse a long message to a clamped, expandable bubble ([5c8f209](https://github.com/punyamsingh/svelte-ui-components/commit/5c8f2097636e915136efc1f8230f5deb88e0bc4b))
-
fix(Menu): add usePortal so the dropdown escapes overflow-clipping ancestors ([af4b7a5](https://github.com/punyamsingh/svelte-ui-components/commit/af4b7a596a9d1f729abc783faf3987686d69d0f3))
-
feat(pie-chart): register sui-pie-chart as a web component ([8e2bbc4](https://github.com/punyamsingh/svelte-ui-components/commit/8e2bbc4390e946dca9bfc55313519757dfce8a2d))
-
fix(MarkdownText): scroll a wide table in a focusable wrapper, not the table ([5cb4df4](https://github.com/punyamsingh/svelte-ui-components/commit/5cb4df477ae1600b2cfe8a9dd77ad6d507b90a17))
-
feat(card): add attribute passthrough and a root-tag override ([9fdaff1](https://github.com/punyamsingh/svelte-ui-components/commit/9fdaff1b2a4fdd594d2871eb9c04554682c40346))
-
test(wc): record the 91 wrapper props that shadow native event handlers ([3d16f17](https://github.com/punyamsingh/svelte-ui-components/commit/3d16f17839f8a6403b5d8db81f9991c1302d51b9))
-
feat(ChatMessage): mark a turn with a leading accent bar via `marker` ([713ec88](https://github.com/punyamsingh/svelte-ui-components/commit/713ec8849bec8aabca940ac793e983dfba7b9135))
-
feat(Table): icon-capable button cells — TableButtonCellData.iconUrl + ariaLabel, icon-only ghost rendering ([1f4a91d](https://github.com/punyamsingh/svelte-ui-components/commit/1f4a91d3dfdd531de3a9292989aef2cd3101eb92))
-
test(forms): isolate form-association contracts from docs demos ([61b388d](https://github.com/punyamsingh/svelte-ui-components/commit/61b388de49804e35161f6838ba71227e5e5fd974))
-
fix(stat-card): let StatCard decide which value animates, in the custom element too ([08c7ea4](https://github.com/punyamsingh/svelte-ui-components/commit/08c7ea477c4ce6d6d7cffe5158b11953dc27e463))
-
feat(ChatSuggestions): structured suggestions, scroll/vertical layouts, loading state, chip theming hooks ([4e2cef4](https://github.com/punyamsingh/svelte-ui-components/commit/4e2cef4bd35ce68a8f0eddba6a2c0da4311b1a9b))
-
fix(a11y): close the fifteen open review findings from the component-reuse PRs ([69c035e](https://github.com/punyamsingh/svelte-ui-components/commit/69c035e9e4d600f69f5f63357490bc9b649f0985))
-
feat(markdown-text): optionally unwrap a whole-body markdown fence ([2588d8f](https://github.com/punyamsingh/svelte-ui-components/commit/2588d8fa4729da3100e6dc494bb89009554af564))
-
feat(toolbar): expose row-layout variables so it can serve an in-flow page header ([6bb210c](https://github.com/punyamsingh/svelte-ui-components/commit/6bb210cfc8932873b4debe0de4ea55eca4f607b2))
-
fix(a11y): name every control that Menu and Checkbox left anonymous ([f576063](https://github.com/punyamsingh/svelte-ui-components/commit/f576063211ea9eed14a22c3ec09f3bee1824dfb7))
-
feat(status): add descriptionSnippet, children, and panel CSS variables ([7b15192](https://github.com/punyamsingh/svelte-ui-components/commit/7b151928aebc621c392394dfa0299c3837f74ddf))
-
feat(FileDropzoneTrigger): add shared trigger visuals for FileInput dropzones ([9e27683](https://github.com/punyamsingh/svelte-ui-components/commit/9e27683931b31b4c488919a9d167884b0d9ffa59))
-
fix(table): let the built-in paginator controls wrap in a narrow container ([5e76791](https://github.com/punyamsingh/svelte-ui-components/commit/5e76791e9c74a5f3df8bab6fdcdb224d07072b3e))
-
feat(card,pill): warn in dev when an attrs entry is discarded ([dd01fe2](https://github.com/punyamsingh/svelte-ui-components/commit/dd01fe2f3bdbfdd035136827b8ae9fa22855cbe9))
-
feat(hitl): add extra actions and a children snippet for multi-action approval ([ab8ab96](https://github.com/punyamsingh/svelte-ui-components/commit/ab8ab96b3736e302db361a859e89f70ef8211892))
-
fix(test): derive Playwright's port from the checkout instead of fixing it ([72adbbd](https://github.com/punyamsingh/svelte-ui-components/commit/72adbbdf2db2686c88e54ec819ff195a577d4eb9))
-
fix(SankeyChart): single global px-per-value scale so ribbons stay flush inside node bars ([5acac8b](https://github.com/punyamsingh/svelte-ui-components/commit/5acac8b5380b07e6ac22f1cc871a4dcd60a69b85))
-
feat(sheet): add a centered dialog variant and a real heading option ([481ecd4](https://github.com/punyamsingh/svelte-ui-components/commit/481ecd4424eb443be86bee152d297533626a7f9e))
-
fix(Progress): progressbar ARIA ([db0d86c](https://github.com/punyamsingh/svelte-ui-components/commit/db0d86c26c0fddba21ef5a3b2801d8b4823a1e4f))
-
fix(a11y): announce Input validation errors and let ChipInput be named ([c492919](https://github.com/punyamsingh/svelte-ui-components/commit/c4929198984e9bc4adecee699a4545aebec76683))
-
fix(typewriter): honour prefers-reduced-motion, matching ChatController ([c34b93f](https://github.com/punyamsingh/svelte-ui-components/commit/c34b93f2c32fff159e9a225aa1b93b7b1062fe38))
-
feat(tabs): vertical orientation, blue default status dot, section labels ([71baf05](https://github.com/punyamsingh/svelte-ui-components/commit/71baf05228c9e0f8092845c9b815caa2e6c3c393))
-
fix(status): stand in for the default icon when its file is absent ([d96be5a](https://github.com/punyamsingh/svelte-ui-components/commit/d96be5acd0fed1c0d499b33d77dad47b6807e921))
-
fix(release): gate the publish on tests, and stop two releases racing ([6d90a10](https://github.com/punyamsingh/svelte-ui-components/commit/6d90a10117a9acbea81600a20db07e82723ecb88))
-
feat(pill): add a semantic tone prop, and stop assuming every pill is clickable ([d1f3178](https://github.com/punyamsingh/svelte-ui-components/commit/d1f317840f2981c0c5220b425b26e908d3f3e9ba))
-
feat(snippet): configurable copy feedback and unmount-safe reset timer ([23b4900](https://github.com/punyamsingh/svelte-ui-components/commit/23b4900593b4b33a5a74aa6759ee52bbe9215672))
-
fix(LineChart): gap-resilient paths for sparse series + 6-tick x-axis cap ([4376152](https://github.com/punyamsingh/svelte-ui-components/commit/43761522f9fa50add602b877808ad20efe38cc78))
-
fix(a11y): bring default label and banner text to AA, and announce the orb's state ([4d9f83f](https://github.com/punyamsingh/svelte-ui-components/commit/4d9f83f59d8232d24b6b2909474795df28f3c813))
-
build(deps): bump @vitest/mocker ([93e0577](https://github.com/punyamsingh/svelte-ui-components/commit/93e057712a9361b6d3afc4c25597858fdac52848))
-
fix(accordion): expanded panel keeps zero height inside a grid parent ([4ba6957](https://github.com/punyamsingh/svelte-ui-components/commit/4ba6957ad2691c2ff7d8d66ad07ae9adc0d2ee60))
-
feat(Card): anchor rendering mode ([fe085a0](https://github.com/punyamsingh/svelte-ui-components/commit/fe085a099169bca05c098e4a9ab7a8c49b23b2ad))
-
fix(BrandLoader): namespace its CSS vars ([4ed5432](https://github.com/punyamsingh/svelte-ui-components/commit/4ed5432ad78b1b002eaef585b7424ea63c505120))
-
fix(tests): make two timing-dependent specs independent of machine load ([fa85a5f](https://github.com/punyamsingh/svelte-ui-components/commit/fa85a5f82382b5e4c346df8875bff76479301933))
-
docs(BarChart): document and test the already-shipped valueLabel override ([6a750a7](https://github.com/punyamsingh/svelte-ui-components/commit/6a750a7499b7fa17e377dea01996b9ba2908762a))
-
fix(Carousel): spread slide properties, plus doc cross-references and a naming fix ([2fd59e1](https://github.com/punyamsingh/svelte-ui-components/commit/2fd59e16bc8baa0f43ab1b03a9c7d3098cf3c314))
-
feat(table): let callers name the controls Table generates itself ([af55682](https://github.com/punyamsingh/svelte-ui-components/commit/af556823ecea557cc1a9a4c874c3358e5bb22e6f))
-
fix(select): preserve viewport fitting for auto placement ([607f693](https://github.com/punyamsingh/svelte-ui-components/commit/607f693ef2cd8fda3fcec9a48a54e0318c9adc50))
-
fix(Carousel): restore the properties-bag contract and announce slide changes ([996511f](https://github.com/punyamsingh/svelte-ui-components/commit/996511f9a435472d3a0dc088c2e800393f9c02fe))
-
feat(toolbar): add backHref to render the back control as a real link ([17d3bac](https://github.com/punyamsingh/svelte-ui-components/commit/17d3bac78e317f5d02da586a5471e40cd968afeb))
-
feat(modal): forward aria-label and role to sui-modal's content panel ([754694c](https://github.com/punyamsingh/svelte-ui-components/commit/754694cf563aee87eedc68be7b3403b69386a710))
-
docs(pill): document the dark-theme recipe, and stop the demo silently killing tone ([1587358](https://github.com/punyamsingh/svelte-ui-components/commit/1587358f03a2df10eedc43d0eb5c339eb310d9d7))
-
fix(Accordion): link trigger to its panel with aria-controls ([ae2d588](https://github.com/punyamsingh/svelte-ui-components/commit/ae2d5889ff53f17ace5b54df951993145e5dcd98))
-
fix(Modal): only treat header.leftImage as a control when a click handler is supplied ([aadd6b6](https://github.com/punyamsingh/svelte-ui-components/commit/aadd6b62e8cf784987b5746e959403a517c6366b))
-
fix(visual): stop a fractional capture box flipping the baseline by a pixel ([4a92b3e](https://github.com/punyamsingh/svelte-ui-components/commit/4a92b3eec98dc4e3a7b1c1d5222499835c995a3e))
-
feat(emptystate): add density variant and --empty-state-align-items ([d88bceb](https://github.com/punyamsingh/svelte-ui-components/commit/d88bceb15b86ad1ecf536d28670c00c9d496a16e))
-
feat(markdown-text): let a consumer add a class to the table wrapper ([5a2b18f](https://github.com/punyamsingh/svelte-ui-components/commit/5a2b18f7c0d477564d4c3c9b0179e61d7c4c98d8))
-
fix(wc): restore the type coverage the host-reserved rename removed, and gate it ([d6066e9](https://github.com/punyamsingh/svelte-ui-components/commit/d6066e9ef3ddc6eabce7b1e5713493f89c42fb50))
-
feat(events): warn once, in dev only, when a deprecated prop spelling is used ([5107b4b](https://github.com/punyamsingh/svelte-ui-components/commit/5107b4bfcda2d2638c5ac4ad5ab459d973b01cf6))
-
fix(docs-contract): skip reference pages that document no single component ([1533adb](https://github.com/punyamsingh/svelte-ui-components/commit/1533adbe42020ddd5fa77b217b3620f91fb3cee1))
-
fix(SplitInput): distribute whole-code autofill into single-char fields ([3396b71](https://github.com/punyamsingh/svelte-ui-components/commit/3396b711563dd9c8c6a9bd60c3192caa205c24a4))
-
fix(stat-card): support value snippets through the WC bundle ([3893440](https://github.com/punyamsingh/svelte-ui-components/commit/3893440ee9b5f7bc3433991b3c53af78d16990c8))
-
feat(pill): let a consumer put arbitrary attributes on the root ([d4c8a91](https://github.com/punyamsingh/svelte-ui-components/commit/d4c8a914ca04cf88570bf239a8097bb429413336))
-
feat(Card): add titleSnippet and descriptionSnippet ([f6b2cbf](https://github.com/punyamsingh/svelte-ui-components/commit/f6b2cbf49ac6cad1edb42b43a34c880e98abdab6))
-
test(visual): state the per-pixel threshold, and pin the colours it cannot see ([3c8112c](https://github.com/punyamsingh/svelte-ui-components/commit/3c8112c85b606e383c7e396c604b28ce97c4e78e))
-
feat(Modal): add entryAnimation and overlayFadeIn props for centered slide-up dialogs ([7a0a964](https://github.com/punyamsingh/svelte-ui-components/commit/7a0a964b5069480c5c1de698db8ba90f79b3b05b))
-
fix(chat-message): scroll a wide table in the wrapper, not the table itself ([ae68890](https://github.com/punyamsingh/svelte-ui-components/commit/ae6889013569f91756f6de6fe30e4517ac9878b4))
-
fix(Input): give helper text its own color, bring error text to AA contrast ([ad30c04](https://github.com/punyamsingh/svelte-ui-components/commit/ad30c04183b75656b4861a66d081ce44fc1263f6))
-
feat: fill component gaps blocking Lighthouse migration ([a1c1f15](https://github.com/punyamsingh/svelte-ui-components/commit/a1c1f15c2466ba776925a00267b418cec9e421cb))
-
feat(SankeyChart): tokenize label typography and first-column label side ([1f8857c](https://github.com/punyamsingh/svelte-ui-components/commit/1f8857c822b2811cdf7b72080dff263df5fece3e))
-
fix(release): abort a release whose build is already stale, and clear the MCP advisories ([a3dcc92](https://github.com/punyamsingh/svelte-ui-components/commit/a3dcc920415f856ade3481f90d7bf3877efe15dc))
-
feat(ChatBubble): decouple launcher width/height tokens for pill launchers ([11de1fe](https://github.com/punyamsingh/svelte-ui-components/commit/11de1fed2eaff0a59774ce1c7a86e8273475dc63))
-
fix(release): publish the MCP package before writing its release landmark ([1811375](https://github.com/punyamsingh/svelte-ui-components/commit/1811375479a639afa072ee475a49e2b9b0ef0ec8))
-
fix(release): stop a truncated history window inflating the version bump ([21509ac](https://github.com/punyamsingh/svelte-ui-components/commit/21509acb22bd1030b838bc7ecddcf29d9f4e0f28))
-
feat(Select,Tabs,FileDropzoneTrigger,CommandMenu,Status,Table): per-icon colour tokens ([7e9a5fc](https://github.com/punyamsingh/svelte-ui-components/commit/7e9a5fc0744aa5ac5d34f989ac9e2229118a39f8))
-
fix(SplitInput): resolve overtyped digit independently of caret position ([189e161](https://github.com/punyamsingh/svelte-ui-components/commit/189e1619d7b1256cfaa9816c1e5c96f26017c7c7))
-
feat(table): let a consumer choose the container's overflow ([c8e4084](https://github.com/punyamsingh/svelte-ui-components/commit/c8e40844350ac5fcc0da124f0960f39007b6b591))
-
fix(Table): thread usePortal to in-cell Select/Menu so they escape the table's overflow ([4f8d5c3](https://github.com/punyamsingh/svelte-ui-components/commit/4f8d5c37f0ffc2b4a07f140d600ce7ba75f15b11))
-
feat(SankeyChart): edge-to-edge layout — last-column label side, horizontal margin, header clamp ([ee4da01](https://github.com/punyamsingh/svelte-ui-components/commit/ee4da01867a1fc7c91155d5292b4fb3bdf01453d))
-
fix(migrate): bound the whole-repo scan tests on their own timeout, not vitest's default ([e0fa556](https://github.com/punyamsingh/svelte-ui-components/commit/e0fa556506f457302fcc50eb2d9de703e5b16801))
-
fix(Tabs): reserve active-state width ([a0483bc](https://github.com/punyamsingh/svelte-ui-components/commit/a0483bc228bb651178aedec23487c4f2f59585af))
-
test(wc): pin the onclick/onClick attribute collision, and correct the encapsulation claim ([91a53d0](https://github.com/punyamsingh/svelte-ui-components/commit/91a53d0b8fc37dac8eba29bf0cb6d9836dc411a6))
-
fix(wc): stop sui-checkbox shadowing Element.attributes, which broke every instance ([f652776](https://github.com/punyamsingh/svelte-ui-components/commit/f6527768488c5e993927d8d214ed307b58833465))
-
fix(a11y): let callers actually name Input, Checkbox and Menu triggers ([55cb6d9](https://github.com/punyamsingh/svelte-ui-components/commit/55cb6d95ae7acb9095f7de2daf89032446a1a633))
-
fix(ChipInput): let a consuming app's Pill and Input theme reach the chips ([ce626f7](https://github.com/punyamsingh/svelte-ui-components/commit/ce626f74e7f69644efaedf5d58e8ff785c1c8bc2))
-
fix(visual): let the page drain between clock advances, not after all of them ([f0b1be6](https://github.com/punyamsingh/svelte-ui-components/commit/f0b1be655d0f5f5f90ddea6cd17b67c879dbf63b))
-
fix(ChipInput): let a consuming app's Pill size and shape reach the chips too ([14e301c](https://github.com/punyamsingh/svelte-ui-components/commit/14e301cb2ecf7475d4ef9d6dd44a7500ec51f32e))
-
feat(IframeViewer): add credentialless prop and postMessage accessor ([a285e01](https://github.com/punyamsingh/svelte-ui-components/commit/a285e01c662fc8329a8b085ff136b722bf894197))
-
test(input): pin why assigning to a $derived on focus out is not a defect ([0523f87](https://github.com/punyamsingh/svelte-ui-components/commit/0523f87c668f8ca6e4391454e9b9012b239df9ba))
-
fix(markdowntext): guard malformed sanitize options and lower-case the tag allow-list ([3cf493f](https://github.com/punyamsingh/svelte-ui-components/commit/3cf493fbbfce734037595e4c05888473a0ae6937))
-
fix(sankey): reserve a left gutter so first-column source labels render in full ([f6d3164](https://github.com/punyamsingh/svelte-ui-components/commit/f6d31649ecee4619ac48c9d90c379ae0d4fa95a3))
-
feat: add showIndicator prop and enhance indicator styling ([f6a8947](https://github.com/punyamsingh/svelte-ui-components/commit/f6a8947b3bcb5026ad5e73772de0a3fe42170e00))
-
fix(hitl): point the reduced-motion guard at the classes it actually renders ([e4b1635](https://github.com/punyamsingh/svelte-ui-components/commit/e4b16358006c592fd5d7d8475a2f0666ced8c177))
-
ci(release): publish to npm before pushing any release metadata ([fb5a124](https://github.com/punyamsingh/svelte-ui-components/commit/fb5a124baa071377eab5a18b1b028ad3e613d903))
-
fix(deps): declare node types so SvelteKit 2.70 can be adopted ([14ff602](https://github.com/punyamsingh/svelte-ui-components/commit/14ff6027efab55bcc9f479267536b2ab5dcb3138))
-
feat(keyboardinput): add a literal opt-out from KEY_SYMBOLS substitution ([61836d4](https://github.com/punyamsingh/svelte-ui-components/commit/61836d4735f3a035c91f9af1d44969cd846fe902))
-
fix(charts): computeLinearTicks honors the requested count as a hard maximum ([6c28bef](https://github.com/punyamsingh/svelte-ui-components/commit/6c28bef5258d44534c1125dae22d5089c867acf2))
-
feat(BarChart): marginX inset override + value-end-only bar rounding ([f600eda](https://github.com/punyamsingh/svelte-ui-components/commit/f600edade0d572ee8af803cd600f7ec1db7489a7))
-
feat(ColorPicker): expose --color-picker-input-height and hex text-transform ([eeaa993](https://github.com/punyamsingh/svelte-ui-components/commit/eeaa993d27a464cffad247371774a3e0732f3297))
-
fix(ThemeSwitcher): add a pressed state to the toggle button ([0b331e2](https://github.com/punyamsingh/svelte-ui-components/commit/0b331e27520982e6117758957833ed549c6ad987))
-
feat(Button): add brand variant ([ac9cb0f](https://github.com/punyamsingh/svelte-ui-components/commit/ac9cb0f5ca89122ee5531124ee693b826416c825))
-
fix(migrate): stop the doc rename treating a controller option as a component prop ([103bfa3](https://github.com/punyamsingh/svelte-ui-components/commit/103bfa362a5a0f05c50cfaca8724949c09b40fbe))
-
build(deps): bump body-parser ([5a42c2c](https://github.com/punyamsingh/svelte-ui-components/commit/5a42c2c91889a20feeffa7acc4e8508c669387ac))
-
feat(StatCard): design-system trend states and inline comparison denominator — neutral '—' glyph, change:null renders N/A, comparisonValue renders '/ &lt;value&gt;' ([b7578a9](https://github.com/punyamsingh/svelte-ui-components/commit/b7578a903be36b3e97ca117e87602ad06ab592e1))
-
feat(Table): JSON-safe leading icon for input cells via TableInputCellData.iconUrl ([b8e75a3](https://github.com/punyamsingh/svelte-ui-components/commit/b8e75a3e4acb05e4b3161a55fe46b37ccf99b444))
-
chore(lint): catch dead imports in the web-component wrappers ([5b19fb8](https://github.com/punyamsingh/svelte-ui-components/commit/5b19fb84245996e6b141256b7f4c5a3d50038d4d))
-
docs(card): stop documenting figcaption inside as="figure" as valid ([c6f0382](https://github.com/punyamsingh/svelte-ui-components/commit/c6f0382bba13856d66441a7d97fb63706f1280ba))
-
docs(Combobox): fix inputElement docs to describe the real getInputRef() API ([f5eafb8](https://github.com/punyamsingh/svelte-ui-components/commit/f5eafb84d8fb68a110f734d85cb009be42f29a6c))
-
fix(release): push the MCP release before publishing it ([9734c32](https://github.com/punyamsingh/svelte-ui-components/commit/9734c3272ec70919826439ff74dc0bf6a1c0eaaf))
-
feat: BarChartRenderContext.bars — per-bar geometry for overlay annotations ([01f8d32](https://github.com/punyamsingh/svelte-ui-components/commit/01f8d326a90b2edb19d5b7d793a5be083efb8ad4))
-
feat(Table): two-tone sort chevron states from the design system — solid pair assets + active/inactive/hover color vars ([13c6d33](https://github.com/punyamsingh/svelte-ui-components/commit/13c6d33352a48f38bb32eea5336a771920fecadd))
-
fix(demo): serve demo-page media locally instead of from picsum.photos ([4c099e6](https://github.com/punyamsingh/svelte-ui-components/commit/4c099e611b531421989c76c3d5d75d9a50033867))
-
docs(select): document the trigger sizing recipe ([24f3981](https://github.com/punyamsingh/svelte-ui-components/commit/24f3981c35856e8e3ba70318d2dc4e15d262521f))
-
fix(LineChart): paint point markers back-to-front so the first series wins an overlap ([207eb8e](https://github.com/punyamsingh/svelte-ui-components/commit/207eb8ed4c101d538bc6b522cc205b63cc69ece3))
-
fix(DateRangePicker): flip the panel above the trigger when it does not fit below ([d3ccc90](https://github.com/punyamsingh/svelte-ui-components/commit/d3ccc90bbb58ab89bcb8054a912c164933486720))
-
fix(demo): prefix demo-media asset paths with base so Pages prerenders ([031da8a](https://github.com/punyamsingh/svelte-ui-components/commit/031da8a4c5236c116976909e03a0163f4968ce2a))
-
feat(LineChart): per-series dash + single-point flat-line rendering (design-system contracts) ([60d2784](https://github.com/punyamsingh/svelte-ui-components/commit/60d27842135d6efc487aea961950bdde375efd8f))
-
fix(fileinput): open the picker on click of the whole drop zone ([ef294a9](https://github.com/punyamsingh/svelte-ui-components/commit/ef294a9fb6be4348fb0d554d5f5e8caf708194fb))
-
feat(Pill): add --pill-line-height CSS hook ([1e00cd9](https://github.com/punyamsingh/svelte-ui-components/commit/1e00cd9335cead785c929abf4ae9ccdb8e2c5461))
-
ci(release): migrate npm publish to OIDC trusted publishing ([b982270](https://github.com/punyamsingh/svelte-ui-components/commit/b9822705ef3f2d92bb19c49969875be8bea1fd9c))
-
fix(visual): refresh two baselines stale on release, gate hydration, unblock the publish ([9867972](https://github.com/punyamsingh/svelte-ui-components/commit/9867972f42b02018f78300edca045cff9344d45c))
-
fix(visual): allow 12 pixels on task-list only, for one unstable arc edge ([3233a9b](https://github.com/punyamsingh/svelte-ui-components/commit/3233a9b86b99c34f08c35e54e28f591db0b9548c))
-
fix(table): restore focus, handle Escape, and single-source the inline search value ([75b9e26](https://github.com/punyamsingh/svelte-ui-components/commit/75b9e2646b176f800a770cf30bfbc63060459fd7))
-
refactor(Table): keep sort chevron asset color-agnostic like every other icon — currentColor-only SVG, two-tone state painting via component CSS, one shared pair asset ([3d3e58c](https://github.com/punyamsingh/svelte-ui-components/commit/3d3e58ccb1b83c05da0009519e676c3181fd5ca1))
-
fix(choicebox): keep the selected look while hovering a selected card ([1585c28](https://github.com/punyamsingh/svelte-ui-components/commit/1585c28983d843541d39a505a9e5f9e0246b6428))
-
ci(yama): bump the review action to v3.0.4 and migrate the config to its schema ([7c5d525](https://github.com/punyamsingh/svelte-ui-components/commit/7c5d525ebc2c18ec95a5b3385f761e5d89bd30b7))
-
fix: donut centre label fits the hole; StatCard breakdown delta sits inline ([d01ef4a](https://github.com/punyamsingh/svelte-ui-components/commit/d01ef4a28d5349cf40bca360724cc5c88660be9a))
-
docs(roadmap): add the AI/chat primitives section and correct a duplicate entry ([eccaf0b](https://github.com/punyamsingh/svelte-ui-components/commit/eccaf0b3663c415a7988b333d071520f71ec1544))
-
ci: make the Playwright suite an actual merge gate ([e8ca5fb](https://github.com/punyamsingh/svelte-ui-components/commit/e8ca5fbbb3ef0f79ab8688bd8d573158ee80ab76))
-
feat(Toast): add --toast-bottom CSS hook ([2bd864b](https://github.com/punyamsingh/svelte-ui-components/commit/2bd864b2e5036b83ded8a9840dc35ef31e3c9e42))
-
feat(Table): opt-in column highlight via TableColumn.highlighted ([8f023b9](https://github.com/punyamsingh/svelte-ui-components/commit/8f023b985cfd4e0f47a88bc16635e16231d6f4c7))
-
feat(Table): summaryRowIndex — DataGrid-parity summary/period-total row highlight via --table-summary-row-background ([7575890](https://github.com/punyamsingh/svelte-ui-components/commit/7575890ce65677999b9e932bb3ca330ad6cef31b))
-
fix(wc): enumerate host event handlers with touch support, catching four it missed ([69958f7](https://github.com/punyamsingh/svelte-ui-components/commit/69958f7d4da0b739211ff0d483a327eefa6609a3))
-
test(wc): catch a prop declared twice in a customElement props map ([419b921](https://github.com/punyamsingh/svelte-ui-components/commit/419b921ec235b12ddc6e2434a5f4fb0b1ace8ae8))
-
chore(visual): baseline task-list, and measure why the other stays out ([9aa8526](https://github.com/punyamsingh/svelte-ui-components/commit/9aa8526487d2510547ccc8e5353b1dddd885ec59))
-
feat(Modal): accessible-name passthrough for header image buttons ([f9cd7dc](https://github.com/punyamsingh/svelte-ui-components/commit/f9cd7dcebd774c4f08f1699f7b86159938d561b9))
-
docs: cross-reference the five remaining low-severity audit pairs ([79aec19](https://github.com/punyamsingh/svelte-ui-components/commit/79aec19e9eec89c9f00af6e9ac0611ec0be4cbb5))
-
fix: DeltaIndicator renders the trend-line arrow, not a filled triangle ([85bcdb7](https://github.com/punyamsingh/svelte-ui-components/commit/85bcdb79245349a5a8e38ae2613b8d23df1975bc))
-
fix: prefix demo media with the Pages base path so the static build prerenders ([ad93de9](https://github.com/punyamsingh/svelte-ui-components/commit/ad93de99cebc1331cfeffd4a41ee36a85de722a8))
-
feat(LineChart): add yIntegerTicks to snap Y-axis ticks to whole numbers ([ca2b41d](https://github.com/punyamsingh/svelte-ui-components/commit/ca2b41d2836c9d09140b7547a7eb0620c115c2c3))
-
build(deps): bump the npm_and_yarn group across 1 directory with 2 updates ([6a78a19](https://github.com/punyamsingh/svelte-ui-components/commit/6a78a19281bff96a3817a6c94c34d9121c1d91a9))
-
feat(Carousel): dot-nav theming + keyboard access ([ecb7a51](https://github.com/punyamsingh/svelte-ui-components/commit/ecb7a516ae3f0a9a93db0dd382d3e913ace9b1cb))
-
build(deps): bump proxy-addr ([656cb4b](https://github.com/punyamsingh/svelte-ui-components/commit/656cb4b661b54e8e9ea966a514f0bed16a269a49))
-
docs(principles): a token can only reach a state the component paints ([c5770bd](https://github.com/punyamsingh/svelte-ui-components/commit/c5770bd3d1e2d5a8cd88a79758dd3e997c521eaf))
-
fix(demo,ChatBubble): stop binding to a derived, and say why the gap is reset ([2051f11](https://github.com/punyamsingh/svelte-ui-components/commit/2051f11db0e9f089069ab9ad93d2600c11f78348))
-
feat(SankeyChart): tokenized plot backdrop panel ([21f67d5](https://github.com/punyamsingh/svelte-ui-components/commit/21f67d5c6e6ec5d2447d6024e18db9ee9be75cec))
-
feat: StatCard layout tokens — flex-child order, breakdown item direction, heading text-transform ([221bb2f](https://github.com/punyamsingh/svelte-ui-components/commit/221bb2f575d386399ed936e54d3e1c040fa0e6bc))
-
feat(modal): add --modal-overlay-background-color overlay token ([ebe23e0](https://github.com/punyamsingh/svelte-ui-components/commit/ebe23e0a0e6129b02f228fe6ab5a4a8b192e360d))
-
fix(ci): give the release verify job 60 minutes for the integration suite ([59df660](https://github.com/punyamsingh/svelte-ui-components/commit/59df660f8f442ebb2b62ad673d5001e316b2710b))
-
fix(wc): restore prettier formatting on the Combobox wrapper ([3463cb5](https://github.com/punyamsingh/svelte-ui-components/commit/3463cb5fc8137534fc89b3f8b836c9cfeeec15c7))
-
feat: BarChartDataPoint.valueLabel — per-bar value-label override ([633e5a3](https://github.com/punyamsingh/svelte-ui-components/commit/633e5a3170acf76535aeb8fc8ecca26f1d3c9b28))
-
feat(InputButton): expose --input-button-container-width ([62242b1](https://github.com/punyamsingh/svelte-ui-components/commit/62242b191ff98f346c9b90c015e756aa8624d51d))
-
fix(mcp): declare the repository so provenance can be verified ([7b65816](https://github.com/punyamsingh/svelte-ui-components/commit/7b65816606d83a3dad728b24f0e37cec7d7fa2bd))
-
fix(package): enable barrel tree-shaking ([f3fc8f6](https://github.com/punyamsingh/svelte-ui-components/commit/f3fc8f616cf5cc3d1664e023a53da744a7f087b6))
-
docs(select): state both halves of the automatic flip condition ([7d8318f](https://github.com/punyamsingh/svelte-ui-components/commit/7d8318f83afc8ea612c17cdf56e2b471ea59b979))
-
style: wrap DeltaIndicator trend-arrow svg to satisfy prettier ([2207603](https://github.com/punyamsingh/svelte-ui-components/commit/2207603ada136754ea4640227a6fca3d81f94608))
-
docs(LineChart): document the yIntegerTicks prop ([865d5c0](https://github.com/punyamsingh/svelte-ui-components/commit/865d5c0e0bf6a214b31db45316198f424aadd503))
-
test(visual): rebaseline the five chart pages that gained a non-finite demo ([52849db](https://github.com/punyamsingh/svelte-ui-components/commit/52849dba174cf2f5ceb3be15a763cfb7e17a8def))
-
test(visual): refresh the two baselines that still assert the pre-AA colour ([9480135](https://github.com/punyamsingh/svelte-ui-components/commit/9480135ebc92476e657fefbbfbf5c09a37d3b1c7))

## [2.91.2](https://github.com/juspay/svelte-ui-components/compare/2.91.2..2.89.2) - 11 July 2026

A toast is a transient status overlay positioned above page content, and
it frequently lands over drawer/footer CTAs. Until now its whole box was
a hit target for its entire duration, so clicks aimed at the controls
beneath it silently died — surfaced as flaky/broken e2e flows (a
save-success toast covering a drawer's 'Add products' button swallowed
the click that should have opened the product picker) and the same dead
clicks for real users.

The root now defaults to pointer-events: none via the new
--toast-pointer-events token; the close button re-enables its own hit
area (pointer-events: auto), and consumers rendering actionable
bottomContent can opt the whole toast back in with
--toast-pointer-events: auto.

Verified: 94/94 unit tests, svelte-check 0 errors; live demo probe —
the toast computes pointer-events: none and elementFromPoint at the
toast's own center resolves to the button beneath it.

-
feat(Table): align-aware builtin cells and horizontal-scroll edge scrims ([2e402ab](https://github.com/punyamsingh/svelte-ui-components/commit/2e402abb83080c64ca1a217a3d150378e48bf311))
-
fix(Tooltip,PieChart,SankeyChart): action viewport clamping, pie label engine, measured widths ([a513907](https://github.com/punyamsingh/svelte-ui-components/commit/a51390772527a78768d104620ebd92edf49ce77a))
-
fix(SankeyChart,Modal,Tabs): label collision engine, modal viewport cap, fade solid zone ([c772a07](https://github.com/punyamsingh/svelte-ui-components/commit/c772a07c8a17373323387ea2ac3cd0d55f636e33))
-
feat(Menu): add placement prop with viewport-aware auto anchoring ([c0a0ad3](https://github.com/punyamsingh/svelte-ui-components/commit/c0a0ad3ede2453ebc5abac5c3fba06ba349a2932))
-
fix(Toast): click-through by default — stop swallowing clicks meant for content beneath ([19be794](https://github.com/punyamsingh/svelte-ui-components/commit/19be79458611201955e9e7b99f62a698b82498f1))

## [2.89.2](https://github.com/juspay/svelte-ui-components/compare/2.89.2..2.89.1) - 9 July 2026

-
fix(ci): run lint on release pull requests ([dc5b89b](https://github.com/punyamsingh/svelte-ui-components/commit/dc5b89b6ffccdfb48df96b3dc72a2a96b210e9c0))

##
2.89.1 - 9 July 2026

- Tooltip: add `iconPosition` ('leading' | 'trailing', default 'leading') so the icon snippet can sit on either side of the trigger content
- Table: add `headerTooltipIcon` + `headerTooltipPosition` — forward a consumer-supplied icon and bubble placement to the header tooltip; the underline affordance is dropped when an icon is provided
- Table: add `rowNumberLabel` to override the row-number header (defaults to '#')
- Table: add `--table-header-border`, `--table-row-number-align`, `--table-header-justify` tokens
- Select: add `--select-value-align` token for the trigger value/placeholder
- BuiltinCell: add `--table-interactive-width` so input/select cells can fill their column
- All additions are opt-in; every default preserves current rendering, so existing consumers are unaffected

-
feat(charts): Highcharts-grade label, tooltip, and interaction alignment ([a5dcc0f](https://github.com/punyamsingh/svelte-ui-components/commit/a5dcc0f9ac690dd10a5705a731555db68fa439c3))
-
feat: expose chart components ([7a87c7d](https://github.com/punyamsingh/svelte-ui-components/commit/7a87c7d1ba1153ec650799f53249dd8b24238da2))
-
feat: add chart-system — DeltaIndicator, DualAxisBarChart, FunnelChart + chart highlight hook ([40f5449](https://github.com/punyamsingh/svelte-ui-components/commit/40f5449d257d81f6ccc22bb9d43f9a7a0882a923))
-
refactor: upgrade all packages & drop deperecated fixes ([0f3bf58](https://github.com/punyamsingh/svelte-ui-components/commit/0f3bf588461af9d5aaf7a41b827581a3e55d4b66))
-
VERSION: 1.26.0: Releasing version 1.26.0 ([d31c571](https://github.com/punyamsingh/svelte-ui-components/commit/d31c5711a0740c571fff0f553dd9417f2d7ac75d))
-
feat(DateRangePicker): add compound date-range picker with slim snippet API ([1d4a7fe](https://github.com/punyamsingh/svelte-ui-components/commit/1d4a7fe281840d952371b8afca0250ae32c060e0))
-
feat: extend StatCard with rows/breakdown/checkbox/slots; add ProportionBar component ([6e02b08](https://github.com/punyamsingh/svelte-ui-components/commit/6e02b080d421eae8e77c78d64972355f5d6ac816))
-
feat(Table): fix single-select toggle, stable selection IDs, correct onCellChange docs, focus ring, optional enabled ([1ec8a0c](https://github.com/punyamsingh/svelte-ui-components/commit/1ec8a0cb7197e1dd3454d958a8dd6f2237b0066b))
-
feat(Tooltip): add usePortal prop and tooltip action; fix DOM leak, CSS scoping, double-show race ([a6d9153](https://github.com/punyamsingh/svelte-ui-components/commit/a6d9153e799f175a893b4bc8df56632dd48552ee))
-
feat(BarChart): stackNormalize + rounded stacked segments + horizontal scroll ([08dfcfe](https://github.com/punyamsingh/svelte-ui-components/commit/08dfcfe67fbc56060244d60a7e01f231833007c3))
-
fix: address unaddressed review comments across merged PRs ([c18226d](https://github.com/punyamsingh/svelte-ui-components/commit/c18226dc4d8b66df38277bf34f3ee85f70863454))
-
feat: add Card, EmptyState components and inline SVG support for Icon ([2f60cad](https://github.com/punyamsingh/svelte-ui-components/commit/2f60cad1439255da42678e4095ad58b5d3f9dcb5))
-
feat(Stepper): vertical mode + rich per-step status ([8d32c00](https://github.com/punyamsingh/svelte-ui-components/commit/8d32c008eb41f225e4fd9d6c8a1e28fbb6da03dd))
-
feat(DateRangePicker): built-in date inputs + time-of-day selection ([8476b71](https://github.com/punyamsingh/svelte-ui-components/commit/8476b7143816c4e87570904537bac13c5700dcb0))
-
refactor: bump mcp package versions & update node engine ([a1acd8b](https://github.com/punyamsingh/svelte-ui-components/commit/a1acd8b19e40effb2c316e8cf400d19891052b03))
-
feat(Combobox): add multi-select, create, action & limit (reuse, no new component) ([510d2b2](https://github.com/punyamsingh/svelte-ui-components/commit/510d2b2a6b48e4488c7c31e9e4b2bf42e8024fbe))
-
feat(DateRangePicker): add clearable, initialPresetLabel, and preset groups ([0142ab9](https://github.com/punyamsingh/svelte-ui-components/commit/0142ab9ed48e9629b2bbde05619d36fbcb1497ea))
-
ci: Automate release and publishing process ([4225408](https://github.com/punyamsingh/svelte-ui-components/commit/422540846ea55556249d10f0db46cbbfaddcd22b))
-
feat(KeyValue): add read-only label/value detail grid component ([979b26d](https://github.com/punyamsingh/svelte-ui-components/commit/979b26d9c75587dde01b591dcf0ed463753c2fb7))
-
feat: add FileInput component with drag-and-drop, validation, and snippet-driven API ([b36a5ab](https://github.com/punyamsingh/svelte-ui-components/commit/b36a5ab99bfd5b347f67c387b9e8c5094dbcd1e5))
-
feat(Button): add variant, size, icon-only, link & loading API ([f999dc3](https://github.com/punyamsingh/svelte-ui-components/commit/f999dc3b804380c77ecc56ab7e3f6b89ba989659))
-
feat(StatCard): add StatCard component with delta auto-inference and CSS-var theming ([3dd8f12](https://github.com/punyamsingh/svelte-ui-components/commit/3dd8f12a2ee214d4812d7f613d5f6e5984c4cb36))
-
feat(Input): leftIcon/rightIcon snippets + click handlers + mandatory + forceError ([931937a](https://github.com/punyamsingh/svelte-ui-components/commit/931937a64d59f829be5f8a845abe0143b96d484e))
-
feat: add Breadcrumb component with snippet-based API ([e463412](https://github.com/punyamsingh/svelte-ui-components/commit/e463412c5e5bc7b395aef31c10bd4092bef3c2c9))
-
feat(PieChart): semiCircle + legendShowValues ([93a8c47](https://github.com/punyamsingh/svelte-ui-components/commit/93a8c47c2ff93b29296995bdd56ab901924dc117))
-
feat(AreaChart): gradientFill ([48ef662](https://github.com/punyamsingh/svelte-ui-components/commit/48ef662226996696119b1b7982b62e3de3209dc6))
-
feat(LottiePlayer): add Lottie animation player component ([b0003e4](https://github.com/punyamsingh/svelte-ui-components/commit/b0003e434934df39a7374585d2d4b092f799d330))
-
feat: add showSelectAll to Select (multi-select select-all with indeterminate) ([d834f8b](https://github.com/punyamsingh/svelte-ui-components/commit/d834f8b540a3dcd2fd30178ead52c53594282bc0))
-
feat(DateRangePicker): compare standalone trigger ([f1ee96e](https://github.com/punyamsingh/svelte-ui-components/commit/f1ee96ed40221dbe18767b40c4a1b12c4a589eed))
-
feat(Modal): backdrop-filter var + usePortal ([d3f1086](https://github.com/punyamsingh/svelte-ui-components/commit/d3f108654db2dde3bd5726f003bce2e784d050f1))
-
ci(yama): add Yama AI PR review workflow ([9356d24](https://github.com/punyamsingh/svelte-ui-components/commit/9356d24ea1d641b187ae5b97344d2ff7a74d351a))
-
feat(Select): string[] normalization, optionIndicator + bottomContent snippets, bindable open ([a5cbfad](https://github.com/punyamsingh/svelte-ui-components/commit/a5cbfadc8fd3387924f84cd87cbc40448c9f1ec1))
-
feat(Sheet): anchor position tokens, dismissible invisible overlay, ref-counted scroll lock ([5986d04](https://github.com/punyamsingh/svelte-ui-components/commit/5986d044952d6f7b9845a9383710788bdf050eee))
-
feat(IframeViewer): add iframe embed with origin-allowlisted postMessage ([eb40be5](https://github.com/punyamsingh/svelte-ui-components/commit/eb40be506ff17eace2d81de1ebb618012fb637dc))
-
feat(SankeyChart): enriched link tooltip context ([f0a0321](https://github.com/punyamsingh/svelte-ui-components/commit/f0a03219ec88e3abcf481151f80defa9b7f9e6f7))
-
feat(Card): add onclick, CSS vars (width/shadow/height), and consumer recipe for custom layouts ([13306cc](https://github.com/punyamsingh/svelte-ui-components/commit/13306cc5aebad22b3fb9825b50747661e6894cda))
-
refactor(Pagination): slim to cursor/load-more primitive (hasMore + onLoadMore only) ([31866f7](https://github.com/punyamsingh/svelte-ui-components/commit/31866f795c4c2a51d96561ccdf17b36088ee50f4))
-
feat(banner): border-radius/border vars, title snippet, role escape hatch ([f284679](https://github.com/punyamsingh/svelte-ui-components/commit/f284679d9429e93a3e1387460e652d0c34f11b52))
-
feat(Tooltip): add icon and content snippets ([38adfa8](https://github.com/punyamsingh/svelte-ui-components/commit/38adfa8a06ce61bc478235e475b6ba2cf21f5af2))
-
feat(DateRangePicker): add inline time-selection layout ([b68570e](https://github.com/punyamsingh/svelte-ui-components/commit/b68570eaa7f694169989dfd866dca55248eba4f1))
-
fix(DualAxisBarChart): add minBarHeight, margin, and tooltipPortal props ([8717450](https://github.com/punyamsingh/svelte-ui-components/commit/87174509f5c68757dabc57a0adc57f48ebd31991))
-
feat(table): add paginatorSlot, getRowTestId/getCellTestId callbacks, and footer CSS vars ([75e7725](https://github.com/punyamsingh/svelte-ui-components/commit/75e7725daf03982269c353c60b2508889a92a94a))
-
feat(Card): headerRight, footer, stretch, scrollable ([f01e98d](https://github.com/punyamsingh/svelte-ui-components/commit/f01e98ddf19453911b559f3c187caea072eace78))
-
fix(BarChart): size the horizontal category-axis gutter to the widest label ([26d2456](https://github.com/punyamsingh/svelte-ui-components/commit/26d24563ee04e0b6098e41e61eb3a22f01823d06))
-
feat(Input): add textarea ergonomics (rows, auto-resize, resize, counter) ([8dfe166](https://github.com/punyamsingh/svelte-ui-components/commit/8dfe166abde2d28910d724f9b5d2a06e492cfe09))
-
fix(components): StatCard tooltip icon affordance + checkbox alignment, chart max-height defaults, bar chart edge margins, delta color inherit ([bb2b660](https://github.com/punyamsingh/svelte-ui-components/commit/bb2b6605def6e4481400e3abbdae8dc787afa989))
-
feat: add opt-in SVG inlining and transform hook to Img ([2861b96](https://github.com/punyamsingh/svelte-ui-components/commit/2861b96404110385609dbf16b9c0f0ca161638a5))
-
feat(Badge): standalone count-bubble (image optional) ([73bc82b](https://github.com/punyamsingh/svelte-ui-components/commit/73bc82b83de7e50e75c649036796065f02c8bb02))
-
feat(Toolbar): expose content-row geometry tokens ([a990e9d](https://github.com/punyamsingh/svelte-ui-components/commit/a990e9d753584a9273c9a628218cffa4ea580e6a))
-
feat(Tabs): --tabs-item-border CSS variable ([5ebcc57](https://github.com/punyamsingh/svelte-ui-components/commit/5ebcc572339458e86486a35ed8b9f8e27ef60a8a))
-
feat(Select): render multi-select option indicator as a design-system checkbox box ([ee07a2e](https://github.com/punyamsingh/svelte-ui-components/commit/ee07a2ea9b3cb6deefc7645b6a3c6972c242a1d5))
-
fix(tooltip): make viewport clamp lint-compliant and flip on main-axis overflow ([0eed291](https://github.com/punyamsingh/svelte-ui-components/commit/0eed2911594f4aa9a3050305cdcecc4b78d1bbd9))
-
feat: animate Tabs underline indicator (slide between tabs) ([ebdd56f](https://github.com/punyamsingh/svelte-ui-components/commit/ebdd56fb0c843cb8523035d361e3a950b441e846))
-
feat(Table): pass sort-stable originalIndex to cell callbacks ([2d6899e](https://github.com/punyamsingh/svelte-ui-components/commit/2d6899ea43994fee2d0bd4e004dc4be83281b335))
-
Build(deps-dev): bump @sveltejs/kit from 1.30.4 to 2.20.6 ([4330b26](https://github.com/punyamsingh/svelte-ui-components/commit/4330b26526fa1ef476cc0fc5289f2e5611c7900c))
-
feat(Accordion): trigger snippet, triggerClasses, ontoggle, testId + a11y ([ba9fd5e](https://github.com/punyamsingh/svelte-ui-components/commit/ba9fd5e4f65b56a332c877e71e62affc7ff6ad89))
-
feat(Pill): add leadingIcon snippet slot and expose leading-icon WC slot ([f703573](https://github.com/punyamsingh/svelte-ui-components/commit/f70357362ced528dc040a355eb4d6acf6c570358))
-
feat(EmptyState): make description optional and add testId prop ([f795025](https://github.com/punyamsingh/svelte-ui-components/commit/f795025dcdaaec4c5a77cdccd8d41c7ea63a2f1d))
-
feat(Select): onOpen/onClose callbacks + ghost variant ([10da22c](https://github.com/punyamsingh/svelte-ui-components/commit/10da22c8af3848c258a15c51b015cbd6aa7ec2d9))
-
feat(EmptyState): add titleSnippet and descriptionSnippet snippet props ([5f78709](https://github.com/punyamsingh/svelte-ui-components/commit/5f78709808b7c2f6b696a68bd8a598f215d80356))
-
feat(Button): add state box-shadow and active-background CSS variables ([bf02b1a](https://github.com/punyamsingh/svelte-ui-components/commit/bf02b1a37ef04c670fb67b50d9627579a83cbca6))
-
feat(Select): add CSS variables for dropdown horizontal sizing ([f28d021](https://github.com/punyamsingh/svelte-ui-components/commit/f28d0216e68625bacff8f85a6bff3de82f1c8be0))
-
feat(Select): add triggerSummary snippet for compact multi-select trigger ([9e2ba79](https://github.com/punyamsingh/svelte-ui-components/commit/9e2ba79f04278d38cb5f7d261c6ae14779aff9a3))
-
feat(InputButton): mandatory, size, external error ([c3bfb7d](https://github.com/punyamsingh/svelte-ui-components/commit/c3bfb7df53e19dd5c807ae4491e6b699eb9055d3))
-
feat(Select): add leftIcon prop for a leading trigger icon ([c01d2c1](https://github.com/punyamsingh/svelte-ui-components/commit/c01d2c111a86beacb0ec19209a40c200c9fdc8dc))
-
fix(sankey,button,menu): QA-blocker fixes from the Breeze dashboard triage ([1f83c5e](https://github.com/punyamsingh/svelte-ui-components/commit/1f83c5e70f97aea94694d595c9d238ad1c240460))
-
feat: add hasMore + prevButtonTestId + nextButtonTestId to Pagination ([328c9af](https://github.com/punyamsingh/svelte-ui-components/commit/328c9afaae7f7bc6cfd14144a3438e384ebdcc32))
-
fix(Tabs): reorder string-branch guard before activeIndex mutation ([d42ed75](https://github.com/punyamsingh/svelte-ui-components/commit/d42ed753df173c7dad058119732fb9d18a9bdbff))
-
feat(Status): add an icon snippet slot for custom media ([d94ff2a](https://github.com/punyamsingh/svelte-ui-components/commit/d94ff2a23c73f212b5333fe60120a82ec7387ff7))
-
feat(Slider): add labelFormatter prop and thumb opacity CSS vars ([96153b8](https://github.com/punyamsingh/svelte-ui-components/commit/96153b8d5b2be8f9aad5a48be283f6a4359a3032))
-
feat(DateRangePicker): opt-in checkmark on the active preset ([9907a55](https://github.com/punyamsingh/svelte-ui-components/commit/9907a55380ffb9e6dee9610c701788c7e9474156))
-
test(DateRangePicker): regression test for same-day preset highlight ([9bff71f](https://github.com/punyamsingh/svelte-ui-components/commit/9bff71fa978761fda88d0178523e44ef9a424d53))
-
feat(DateRangePicker): add presetToggle to deselect the active preset ([e354bdc](https://github.com/punyamsingh/svelte-ui-components/commit/e354bdc79966170c49240b8902a4937a8d2b141f))
-
feat: add rowsDirection to StatCard for horizontal section layout ([26316fb](https://github.com/punyamsingh/svelte-ui-components/commit/26316fb9fff33264e557155a6cf9e883bef4d0b5))
-
feat(DateRangePicker): expose timeSelectionLayout on the web component + document it ([81518e7](https://github.com/punyamsingh/svelte-ui-components/commit/81518e7f26e0a48ff69acb5663ed1d294fd16883))
-
feat(Gauge): fix NaN/Infinity on max=0, add max+labelFormatter props ([c2786ae](https://github.com/punyamsingh/svelte-ui-components/commit/c2786ae585ed55850b7fd1aec2d5b20d7976917a))
-
Build(deps-dev): bump vite from 4.5.0 to 4.5.2 ([e45d359](https://github.com/punyamsingh/svelte-ui-components/commit/e45d359f62b979ca47113a705e5a656c16b6e0fd))
-
feat(SplitInput): pass autoComplete and inputMode through FieldConfig ([142a4ff](https://github.com/punyamsingh/svelte-ui-components/commit/142a4fff56dd3955be35f2b7616d9356962412b3))
-
fix(Checkbox): keep the native input's checked state in sync on label clicks ([ee2b616](https://github.com/punyamsingh/svelte-ui-components/commit/ee2b61666be2643d750d9de01e5a4a4f6c579542))
-
Build(deps-dev): bump vite from 4.5.13 to 4.5.14 ([1ee024c](https://github.com/punyamsingh/svelte-ui-components/commit/1ee024c729db4867634498a5dc8effb047cc5bef))
-
fix(DateRangePicker): keep the committed preset highlighted across the open cycle ([81b2753](https://github.com/punyamsingh/svelte-ui-components/commit/81b2753cf8b7f550bcb27b867e67af0a3071c098))
-
feat(Sheet): add onafteropen + onafterclose lifecycle callbacks ([bbe65dd](https://github.com/punyamsingh/svelte-ui-components/commit/bbe65ddf7fabcc4942c8745fc19043d477711afa))
-
feat: add textViewTransformers in Input and rightIcon in InputButton ([284ca62](https://github.com/punyamsingh/svelte-ui-components/commit/284ca623a565eda20ff2b0db9ea45475cd110085))
-
Build(deps-dev): bump vite from 4.5.9 to 4.5.11 ([68dfe96](https://github.com/punyamsingh/svelte-ui-components/commit/68dfe96d98e17ea46b6e15200f0722dced05cd3f))
-
feat(LoadingDots): add --loading-dots-pulse-min-scale token for breathing pulses ([2f81f62](https://github.com/punyamsingh/svelte-ui-components/commit/2f81f629ca40306e382630bf428080a187caa745))
-
feat(Select): document itemTestId/dropdownAlign/triggerSummary + expose itemTestId in wc wrapper ([9f97377](https://github.com/punyamsingh/svelte-ui-components/commit/9f97377dd82b2731e9dde12020328d618df0e84e))
-
feat(Toggle): disabled prop ([975f842](https://github.com/punyamsingh/svelte-ui-components/commit/975f842553eedfc92fa735dac6559f2240fcef65))
-
feat(Table,Tooltip): opt-in header tooltip icons, row-number label, and configurable cell alignment/width ([86e0731](https://github.com/punyamsingh/svelte-ui-components/commit/86e073189befe0f82d98437b0687e555d7777bed))
-
feat(Toast): Fix the auto-dismiss timer to RESTART when the message/props change ([70899ab](https://github.com/punyamsingh/svelte-ui-components/commit/70899ab8d47f5b1c2adaec1aa2de6594f53a681e))
-
feat(Toolbar): add testId + headingTestId props ([0d9b68c](https://github.com/punyamsingh/svelte-ui-components/commit/0d9b68cb1ce750cd1dfa733dd4509751021c3c2a))
-
Build(deps-dev): bump vite from 4.5.11 to 4.5.13 ([b2ca76f](https://github.com/punyamsingh/svelte-ui-components/commit/b2ca76f85031f3ac1d36640c615f41c50c6bf6ca))
-
Build(deps-dev): bump vite from 4.5.3 to 4.5.5 ([0c85503](https://github.com/punyamsingh/svelte-ui-components/commit/0c855030abfcc45c3bf3445ea1723e1966f05c82))
-
Build(deps-dev): bump vite from 4.5.2 to 4.5.3 ([34e0404](https://github.com/punyamsingh/svelte-ui-components/commit/34e0404c7dac3432a93ff205fc84a2621e1433aa))
-
feat(EmptyState): add CSS variables for actions container layout ([a6cb4d9](https://github.com/punyamsingh/svelte-ui-components/commit/a6cb4d9d1b2b38bee943a8d083ee17b7e9f9bd78))
-
feat: add testId, onclick (interactive-div), and focus CSS vars to Card (slim follow-up to #210) ([40a9d1e](https://github.com/punyamsingh/svelte-ui-components/commit/40a9d1eb1a480984b8f68cf7f7375152911c38c6))
-
feat: Expose CSS variables for Brand Loader ([8067db5](https://github.com/punyamsingh/svelte-ui-components/commit/8067db5ac140434bb06d91fe9171bd51a182a45b))
-
feat(DateRangePicker): report selected preset label in apply events ([c19fce0](https://github.com/punyamsingh/svelte-ui-components/commit/c19fce05055e50f78707bf27b316c6f3c5c7aa39))
-
feat(Button): add pointer-event props for hold-and-release interactions ([4254fcc](https://github.com/punyamsingh/svelte-ui-components/commit/4254fcce25277e15af81d0639a679be8b30a0601))
-
fix(StatCard): render subtitle alongside rows ([f31cc1d](https://github.com/punyamsingh/svelte-ui-components/commit/f31cc1da39b63753680156f5d586bb4df054dbf3))
-
fix: update badge & toolbar defaults ([157331a](https://github.com/punyamsingh/svelte-ui-components/commit/157331af72a8959dd2b9e2d579a62a86c58749e9))
-
feat(Select): add dropdownAlign prop to right-anchor the dropdown panel ([f814601](https://github.com/punyamsingh/svelte-ui-components/commit/f81460147df77572326f95279175c9cb2c6f4ac2))
-
feat(DateRangePicker): add maxRangeDays to cap selectable range span ([3ddda22](https://github.com/punyamsingh/svelte-ui-components/commit/3ddda22a472a4f2e5cd04fa98df46cd33d0faeba))
-
feat(modal): falsy-guard fixes, redundant-guard removal, expose --modal-header-align-items ([f1f5037](https://github.com/punyamsingh/svelte-ui-components/commit/f1f5037c0203ec8db929d8999032acb385bce3de))
-
fix(Button): address PR review feedback ([e9b94cc](https://github.com/punyamsingh/svelte-ui-components/commit/e9b94cce52937e68149f61b282f0c4fcba521f19))
-
feat(Status): fix vertical centering by making .background the flex layout container ([30be191](https://github.com/punyamsingh/svelte-ui-components/commit/30be19173e089194467d5875b814c48b3b3c3ff3))
-
feat(Table): cut the keyed-column minor release — lint fixes for the absorption train ([19a521f](https://github.com/punyamsingh/svelte-ui-components/commit/19a521f1354a43165fcb36eea6e329d71093d02b))
-
feat(Table): pass sort-stable originalIndex to onRowClick and getRowId ([8778e12](https://github.com/punyamsingh/svelte-ui-components/commit/8778e1286f03d2a40a20f54072c4ca20b1959671))
-
fix: resolve prettier/eslint lint failures blocking the release publish pipeline ([c5ddd5f](https://github.com/punyamsingh/svelte-ui-components/commit/c5ddd5f34d7a50282f6fbbe5671f84e02bec4c2b))
-
feat(Modal): expose disabled-state vars for footer buttons ([c2c7a09](https://github.com/punyamsingh/svelte-ui-components/commit/c2c7a095e7fec1d618f364930fc27b69aa47bb07))
-
Build(deps): bump micromatch from 4.0.5 to 4.0.8 ([41f9768](https://github.com/punyamsingh/svelte-ui-components/commit/41f9768bd10622da1c5bf6b46971b6e88fd29515))
-
feat(Card): add cssVars prop for per-instance CSS variable injection ([f7811e4](https://github.com/punyamsingh/svelte-ui-components/commit/f7811e4b415560853c0c91ada9e64db50a4e3e8d))
-
docs(Input): demo horizontal and both resize options ([3a84a48](https://github.com/punyamsingh/svelte-ui-components/commit/3a84a4841fe8248edd83f66771b40e2bb2f6930b))
-
fix(modal,toast): inline header/toast icon SVGs so currentColor inherits ([ab41494](https://github.com/punyamsingh/svelte-ui-components/commit/ab4149470b304725a8dac719e07e3cb632bcdcc2))
-
fix(Table): forward itemTestId through select cells so options keep their data-pw contract ([8c2faa8](https://github.com/punyamsingh/svelte-ui-components/commit/8c2faa85b710aba33a0d2358cfc6a00fa566b971))
-
feat(Img): add testId prop (slim split from #218) ([afe1f7e](https://github.com/punyamsingh/svelte-ui-components/commit/afe1f7e9f177f4d48df04afbdbc22d08784e0d24))
-
feat: add carousel test ids ([4c9ca57](https://github.com/punyamsingh/svelte-ui-components/commit/4c9ca576daa67b7cc701c7c49ca4605859b87a28))
-
fix: resolve onstatechange input callback not triggered ([f30f72b](https://github.com/punyamsingh/svelte-ui-components/commit/f30f72bcfb37870dd357addc1eb993be335ccf5c))
-
fix(menu,icon): inline SVG item/URL icons so currentColor inherits text colour ([447d221](https://github.com/punyamsingh/svelte-ui-components/commit/447d221bb43cb5d3bbb49a6d2e70d2083077f6e7))
-
Build(deps): bump braces from 3.0.2 to 3.0.3 ([44a7a47](https://github.com/punyamsingh/svelte-ui-components/commit/44a7a47efe584897e433b803da4834155428131c))
-
Build(deps): bump nanoid from 3.3.7 to 3.3.8 ([ce0733a](https://github.com/punyamsingh/svelte-ui-components/commit/ce0733af58c355d418a60bf38d85c2caad17f473))
-
style(modal): prettier formatting for inline header Img tags ([12f36d1](https://github.com/punyamsingh/svelte-ui-components/commit/12f36d11d20402f145cbb4381dbfe5492b2fa44b))
-
BZ:6027: feat: Added support in select component to choose whether to show selected item or not ([1fe8bb6](https://github.com/punyamsingh/svelte-ui-components/commit/1fe8bb6bb3d6ad5f81745c99ebb43e26c0955b09))
-
feat: expose additional CSS variables in Toast component ([8feffab](https://github.com/punyamsingh/svelte-ui-components/commit/8feffab164439b96fe2451e1bfe5d1564af44382))
-
feat(Select): add itemTestId prop + per-option data-pw test hook ([d08cd5d](https://github.com/punyamsingh/svelte-ui-components/commit/d08cd5d9aed247201e5006b0b91bd6410a03db8f))
-
fix(KeyValue): satisfy lint to unblock the release pipeline ([71c8250](https://github.com/punyamsingh/svelte-ui-components/commit/71c82503f084afde0e4ae0b70882b1842b3632af))
-
build(deps): bump hono from 4.12.23 to 4.12.25 in /mcp ([3b95bd4](https://github.com/punyamsingh/svelte-ui-components/commit/3b95bd45ab7f4b8faf4be2f1f14720b832c07ecd))
-
Build(deps): bump cross-spawn from 7.0.3 to 7.0.6 ([c68a344](https://github.com/punyamsingh/svelte-ui-components/commit/c68a344d8fb5347465e148f9f574d642a44eb95a))
-
fix: prevent date picker clipping and restore month navigation ([7a42f64](https://github.com/punyamsingh/svelte-ui-components/commit/7a42f649087c22c6a76ba2ad10ab5c217637fcee))
-
fix(table): sort separator-formatted numeric strings by value, not lexicographically ([83308fb](https://github.com/punyamsingh/svelte-ui-components/commit/83308fb225994bdeb919a5dd3a62492aebbbf6ab))
-
chore: prettier-format button demo page ([dc36907](https://github.com/punyamsingh/svelte-ui-components/commit/dc36907fd4663870fd49cedb8412654d6e23a404))
-
fix(DateRangePicker): reseed time inputs when a preset is selected ([9e9eb68](https://github.com/punyamsingh/svelte-ui-components/commit/9e9eb6885f297ef327429fae9f6e7cff38faf3e3))
-
fix: use effect for Validation State ([e93bf4f](https://github.com/punyamsingh/svelte-ui-components/commit/e93bf4fc4aab691f60be2e6be9bdada614d7b82f))
-
fix(DateRangePicker): match active preset by label, not same calendar day ([c05242e](https://github.com/punyamsingh/svelte-ui-components/commit/c05242e554e8ab81e37b2636a3caf9e9f2e0ca8f))
-
fix: toolbar additional content display ([34ffa11](https://github.com/punyamsingh/svelte-ui-components/commit/34ffa11f9eb27972151f9383f93a6f6b8fdb653f))
-
Build(deps): bump rollup from 3.29.4 to 3.29.5 ([64a648a](https://github.com/punyamsingh/svelte-ui-components/commit/64a648aed89ba394a60b37bf4dfdfe4e82b5e0c5))
-
feat(Table): prettier-reflow BuiltinCell tag to unblock the originalIndex release ([ba947fa](https://github.com/punyamsingh/svelte-ui-components/commit/ba947fa1dc1601e9f51a39f11861a3eb0e2aef0a))
-
style(DateRangePicker): fix prettier formatting to unblock release ([7bcc066](https://github.com/punyamsingh/svelte-ui-components/commit/7bcc066726907ee331aba155a973d9ed973debd7))
-
fix(Select): close multi-select searchable dropdown on trigger click ([9a4ad94](https://github.com/punyamsingh/svelte-ui-components/commit/9a4ad942036073eacf7ca041db858d03d78a54db))
-
fix: make Table default sort icon visible at rest ([e720522](https://github.com/punyamsingh/svelte-ui-components/commit/e720522c8fd8793bc4a7fc9fdcacd40cff4e4089))
-
feat(Checkbox): move aria-controls from aria-hidden input to span[role=checkbox] ([591b432](https://github.com/punyamsingh/svelte-ui-components/commit/591b432fde23d9b23ffa3ed8851d1a82aa9e988f))
-
feat: expose text-wrap CSS vars on Banner ([1bd3870](https://github.com/punyamsingh/svelte-ui-components/commit/1bd3870cc846341f2b964ea46123121fe4bda69c))
-
feat: add testId prop to EmptyState ([0276943](https://github.com/punyamsingh/svelte-ui-components/commit/027694391e599661815c5908be5587f5ea833faa))
-
fix: preventing fading gradient on edge of scroller on mobile ([53b30f9](https://github.com/punyamsingh/svelte-ui-components/commit/53b30f9cbb8191bfa140cb6f859b74c38d05c8ae))
-
feat(Loader): use canonical typeof string guard for data-pw testId ([f3f8042](https://github.com/punyamsingh/svelte-ui-components/commit/f3f8042b8cc202648b2a929bdc535fa96953b232))
-
feat(FileInput): export openFilePicker as callable imperative method ([86e9dbb](https://github.com/punyamsingh/svelte-ui-components/commit/86e9dbb4a0242773a264a0575f1334372a903f3d))
-
fix: Tooltip label color no longer relies on inheritance ([755dd59](https://github.com/punyamsingh/svelte-ui-components/commit/755dd5973402c171bdf5b47b6b6a0f064800cd03))
-
fix(Button): improve default styles for disabled state ([7b04c2b](https://github.com/punyamsingh/svelte-ui-components/commit/7b04c2b72b997439e107e523703dd1a0682b5c4d))
-
fix: default toolbar back icon alignment ([401c2c7](https://github.com/punyamsingh/svelte-ui-components/commit/401c2c744cfd869f9213105e0584c433d82f55f7))
-
- Disable button text if text is empty or null ([4e1202b](https://github.com/punyamsingh/svelte-ui-components/commit/4e1202b7dce14139bd23108f1774f4a7fb1094db))
-
Add css variable for left and right content visibility for list item component ([c084fb2](https://github.com/punyamsingh/svelte-ui-components/commit/c084fb2fa0702a095214c7c2b609743cddde53a1))
-
feat: exposed color, constraints on toolbar text ([6753485](https://github.com/punyamsingh/svelte-ui-components/commit/6753485c39982da2647764b00bccdaac35c0c00a))
-
fix: input field width in input button component ([faeee72](https://github.com/punyamsingh/svelte-ui-components/commit/faeee72e1ab71bc7a30a411021f44dd739f33e53))
-
feat(Modal): add --modal-content-padding token for slot-content body padding ([7e57778](https://github.com/punyamsingh/svelte-ui-components/commit/7e57778cea78325d496b8e3414a174c7a25ec7f1))
-
fix(DateRangePicker): reflect open/closed state in the trigger aria-label ([0553ae8](https://github.com/punyamsingh/svelte-ui-components/commit/0553ae8b116a8c00bfd543a14483a5e60470c160))
-
feat(Button): add --button-min-width CSS variable ([d0b6ac6](https://github.com/punyamsingh/svelte-ui-components/commit/d0b6ac68d5eee270086ea1768cd58dcbab925be3))
-
feat: Support HTML content in button text ([f4cd0b1](https://github.com/punyamsingh/svelte-ui-components/commit/f4cd0b19ca26194fe6d9f2e9668cb94fd190ccbe))
-
chore: release: 1.31.0 ([8ebb5fc](https://github.com/punyamsingh/svelte-ui-components/commit/8ebb5fcdab45dd09e6b35f6e3bf43e2f59691655))
-
chore: released version 1.30.0 ([25dba34](https://github.com/punyamsingh/svelte-ui-components/commit/25dba34e0011367dcfe8e0c779bc9310f72b1ff6))
-
chore: released version 1.29.0 ([1150d7c](https://github.com/punyamsingh/svelte-ui-components/commit/1150d7c260dcf249fd58443fee687246b43a8f05))
-
VERSION: 1.27.0: release version 1.27.0 ([957c348](https://github.com/punyamsingh/svelte-ui-components/commit/957c3482e7b82cdf830c9c0580ab02bc507646d5))
-
feat: added css variables for icon and text display for button ([b7596b0](https://github.com/punyamsingh/svelte-ui-components/commit/b7596b0ef12a005682e6eb1a5791e621ddf78e40))
-
VERSION: 1.21.0 ([a191afe](https://github.com/punyamsingh/svelte-ui-components/commit/a191afe5bc664c60905613490038094f4bc23c5a))
-
VERSION: 1.20.0 ([2b3234c](https://github.com/punyamsingh/svelte-ui-components/commit/2b3234c62cb8462ecaa40b1b8d1cc7347553cac2))
-
feat(Loader): add testId optional prop to LoaderProperties type ([dabc8d6](https://github.com/punyamsingh/svelte-ui-components/commit/dabc8d64861e332a922de19a050a3935ae4e1cc4))
