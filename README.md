## Phases of usage of JS tools

All of these are independent. variations can yield optimizations of course.

### DX - Developer experience

1. Formatter - format code you write acc to a style guide. Comsetic.
2. Linter - static check code, better idioms, highligh security issues.

neither intend to change code. Just displace and refactor.

### Optimize - Technically non-optional

3. Bundler - combine all JS files to generate a single one, essentially. Traditonal browser requirement. Does optimizations like tree shaking (dead code removal). Realistically, takes care of non-JS assets and linkages too.
4. Transpiler - combine modern/fancy JS into lowest-denominator-compatible JS. Originally meant for IE and old browsers when ES6 came about. JSX to JS also happens in this step, if needed.
5. Minification - decrease bundle size by removing whitespace, changing variable names. Optionally, leaves some cryptic tokens in output and generates a "source map". When the capable runtime is presented with both the minified file and source map, it can point out corresponding parts, with step-through precision. very useful for debugging.

## Actual tools (nouns)

1. Formatter - Prettier is opinionated (low config)
   1. Form factor: works as browser plugin.
   2. Easy to use, no setup.
   3. Can auto-format files.
2. Linter - eslint. Can lint static files only (deliberate).
   1. Form factor: CLI tool, pass files to lint.
   2. Simple usage is easy.
   3. Highly configurable. But doesn't need much config due to existence of good presets. A good preset + some exceptions if needed go a long way.
   4. Normal usage generally _requires_ an observer-presenter layer, i.e. a project files "changed" observer generates a stream and passes it to eslint, which returns the results back, which gets presented in the terminal, browser console or mobile device - whatever you're developing. Example of observer-presenter layers: nodemon, create-react-app dev server, vscode ESLint plugin.
   5. Can auto-fix files.
3. Bundler - webpack.
   1. Easy to use in the simple scenario.
   2. Highly configurable
4. Transpiler - babel
   1. Form factor - CLI tool. Input file to output file.
   2. Args: Can specify target JS spec. Inputs non-exact enums. or exact specs, whatever you like.
   3. Handles JSX to JS too. And many other source, target combinations
5. Minification - uglifjs
   1. Form factor: simple CLI, input file to output file.
   2. Has option to generate corresponding source map.

## Fronend vs backend relevance

Frontend projects usually need all steps.
Backend projects can afford to be sloppy for transpilation, since Node.js usually supports JS flavors.
