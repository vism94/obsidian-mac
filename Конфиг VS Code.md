```json
{

// ============================================================

// FILES

// ============================================================

"files.autoSave": "afterDelay",

"files.autoSaveDelay": 800,

"files.exclude": {

"**/node_modules": false,

"**/.git": false,

"**/dist": false,

"**/build": false,

"**/.vite": false

},

  

// ============================================================

// EDITOR - APPEARANCE

// ============================================================

"editor.fontSize": 16,

"editor.fontFamily": "Fira Code, JetBrains Mono, Cascadia Code, Consolas, monospace",

"editor.fontLigatures": true,

"editor.tabSize": 2,

"editor.insertSpaces": true,

"editor.detectIndentation": false,

"editor.wordWrap": "on",

"editor.minimap.enabled": false,

"editor.cursorBlinking": "expand",

"editor.cursorSmoothCaretAnimation": "on",

"editor.smoothScrolling": true,

"editor.guides.bracketPairs": "active",

"editor.guides.indentation": true,

  

// ============================================================

// EDITOR - FORMATTING

// ============================================================

"editor.formatOnSave": false,

"editor.formatOnPaste": false,

"editor.formatOnType": false,

"editor.defaultFormatter": null,

  

// ============================================================

// EDITOR - SUGGESTIONS & HINTS

// ============================================================

"editor.unicodeHighlight.allowedLocales": {

"ru": true

},

"editor.linkedEditing": true,

"editor.suggest.insertMode": "replace",

"editor.suggest.preview": true,

"editor.acceptSuggestionOnCommitCharacter": false,

"editor.acceptSuggestionOnEnter": "on",

"editor.quickSuggestions": {

"other": "on",

"comments": "off",

"strings": "on"

},

"editor.parameterHints.enabled": true,

"editor.hover.enabled": true,

"editor.hover.delay": 400,

"editor.hover.sticky": true,

"editor.hover.above": false,

  

// ============================================================

// EDITOR - CODE ACTIONS ON SAVE

// ============================================================

"editor.codeActionsOnSave": {

"source.fixAll.eslint": "explicit",

},

  

// ============================================================

// EDITOR - FEATURES

// ============================================================

"editor.semanticHighlighting.enabled": true,

"editor.bracketPairColorization.enabled": true,

"editor.inlineSuggest.enabled": true,

"editor.stickyScroll.enabled": true,

"editor.accessibilitySupport": "off",

"editor.inlineSuggest.suppressSuggestions": false,

  

// ============================================================

// JAVASCRIPT

// ============================================================

"javascript.updateImportsOnFileMove.enabled": "always",

"javascript.suggest.autoImports": true,

"javascript.suggest.completeJSDocs": true,

"javascript.inlayHints.functionLikeReturnTypes.enabled": true,

"javascript.inlayHints.parameterTypes.enabled": true,

  

// ============================================================

// TYPESCRIPT

// ============================================================

"typescript.updateImportsOnFileMove.enabled": "always",

"typescript.suggest.autoImports": true,

"typescript.suggest.completeJSDocs": true,

"typescript.preferences.includePackageJsonAutoImports": "on",

"typescript.inlayHints.functionLikeReturnTypes.enabled": true,

"typescript.inlayHints.parameterTypes.enabled": true,

"typescript.inlayHints.propertyDeclarationTypes.enabled": true,

"typescript.inlayHints.parameterNames.enabled": "literals",

  

// ============================================================

// WORKBENCH

// ============================================================

"workbench.colorTheme": "One Dark Pro",

"workbench.editor.closeOnFileDelete": true,

"workbench.editor.highlightModifiedTabs": true,

  

// ============================================================

// TERMINAL

// ============================================================

"terminal.integrated.defaultProfile.windows": "Git Bash",

"terminal.integrated.fontSize": 16,

"terminal.integrated.fontFamily": "Fira Code, JetBrains Mono, Cascadia Code, Consolas, monospace",

"terminal.integrated.cursorBlinking": true,

"terminal.integrated.cursorStyle": "line",

"terminal.integrated.shellIntegration.enabled": true,

"terminal.integrated.smoothScrolling": true,

"terminal.integrated.tabs.enabled": true,

"terminal.integrated.copyOnSelection": true,

"terminal.integrated.allowChords": false,

"terminal.integrated.allowMnemonics": false,

  

// ============================================================

// EXPLORER

// ============================================================

"explorer.confirmDelete": false,

"explorer.confirmDragAndDrop": false,

"explorer.fileNesting.enabled": true,

"explorer.fileNesting.patterns": {

"package.json": "package-lock.json, yarn.lock, pnpm-lock.yaml",

"tsconfig.json": "tsconfig.*.json",

".env": ".env.*",

".gitignore": ".gitattributes"

},

  

// ============================================================

// GIT

// ============================================================

"git.confirmSync": false,

"git.autofetch": true,

"git.pruneOnFetch": true,

"git.allowForcePush": true,

"git.enableSmartCommit": true,

"git.decorations.enabled": true,

"git.blame.editorDecoration.enabled": true,

  

// ============================================================

// EMMET

// ============================================================

"emmet.includeLanguages": {

"javascript": "javascriptreact",

"typescript": "typescriptreact"

},

"emmet.triggerExpansionOnTab": true,

  

// ============================================================

// DIFF EDITOR

// ============================================================

"diffEditor.ignoreTrimWhitespace": true,

"diffEditor.renderSideBySide": true,

"workbench.iconTheme": "catppuccin-perfect-macchiato",

"workbench.editor.enablePreview": false

}
```