```json
{  
  // todo settings: global configurations  
  // ------  
  // Automatic update vs code  
  "update.mode": "default",  
  // ------  
  "telemetry.telemetryLevel": "off",  
  "window.restoreFullscreen": true,  
  "window.commandCenter": false,  
  "extensions.ignoreRecommendations": true,  
  "breadcrumbs.enabled": true,  
  "breadcrumbs.symbolSortOrder": "type",  
  "breadcrumbs.filePath": "on",  
  "breadcrumbs.symbolPath": "on",  
  "editor.renderWhitespace": "none",  
  "editor.minimap.enabled": true,  
  "editor.minimap.size": "fit",  
  "editor.renderControlCharacters": false,  
  "editor.detectIndentation": false,  
  "editor.multiCursorModifier": "ctrlCmd",  
  "editor.tabCompletion": "on",  
  "editor.rulers": [  
    120  
  ],  
  "editor.wordWrap": "bounded",  
  "editor.wordWrapColumn": 120,  
  "editor.snippetSuggestions": "top",  
  "editor.suggestSelection": "first",  
  "editor.cursorSurroundingLines": 5,  
  "editor.smoothScrolling": true,  
  "editor.cursorSmoothCaretAnimation": "on",  
  "editor.lightbulb.enabled": "off",  
  "editor.wordSeparators": "`~!@#$%^&*()-_=+[{]}\\|;:'\",.<>/?",  
  "editor.bracketPairColorization.enabled": true,  
  "editor.bracketPairColorization.independentColorPoolPerBracketType": false,  
  "editor.guides.bracketPairsHorizontal": "active",  
  "editor.guides.highlightActiveBracketPair": true,  
  "editor.guides.highlightActiveIndentation": true,  
  "editor.guides.indentation": true,  
  "editor.guides.bracketPairs": true,  
  "editor.suggest.showStatusBar": true,  
  "editor.stickyScroll.enabled": true,  
  "workbench.tips.enabled": false,  
  "workbench.startupEditor": "none",  
  "workbench.settings.editor": "json",  
  "workbench.tree.renderIndentGuides": "always",  
  "workbench.layoutControl.enabled": true,  
  "workbench.layoutControl.type": "both",  
  "workbench.localHistory.enabled": true,  
  "workbench.localHistory.maxFileSize": 2048,  
  "workbench.editor.tabSizing": "shrink",  
  "workbench.editor.highlightModifiedTabs": true,  
  "workbench.editor.pinnedTabSizing": "shrink",  
  "workbench.editor.enablePreview": false,  
  // ------  
  // todo enable/disable extensions  
  "code-runner.enableAppInsights": true,  
  // ------  
  // todo settings: Folder  
  "explorer.compactFolders": false,  
  "explorer.confirmDelete": false,  
  "explorer.confirmDragAndDrop": false,  
  // todo settings: Files  
  "files.eol": "\n",  
  "files.insertFinalNewline": true,  
  "files.trimFinalNewlines": true,  
  "files.trimTrailingWhitespace": true,  
  "files.exclude": {  
    "**/.git": false  
  },  
  // todo settings: Theme  
  "workbench.colorTheme": "GitHub Dark Dimmed",  
  "workbench.iconTheme": "material-icon-theme",  
  // todo settings: Cursor  
  "editor.cursorBlinking": "solid",  
  "editor.cursorStyle": "block",  
  // todo settings: Font  
  "window.zoomLevel": 0.6,  
  "editor.fontSize": 15,  
  "editor.fontFamily": "JetBrains Mono, Hack, monospace",  
  "editor.fontLigatures": true,  
  "terminal.integrated.fontFamily": "JetBrains Mono, Hack, monospace",  
  "terminal.integrated.fontSize": 14,  
  "debug.console.fontSize": 14,  
  "debug.console.fontFamily": "JetBrains Mono, Hack, monospace",  
  "debug.console.lineHeight": 20,  
  "workbench.fontAliasing": "antialiased",  
  "editor.tabSize": 2,  
  // todo settings: TERMINAL  
  "terminal.integrated.defaultProfile.osx": "bash",  
  "terminal.integrated.profiles.osx": {  
    "bash": {  
      "path": "bash",  
      "args": [  
        "-l"  
      ],  
      "icon": "terminal-bash"  
    },  
    "bash_node_22": {  
      "path": "bash",  
      "args": [  
        "-c",  
        "source ~/.bash_profile; nvm use 22; /opt/homebrew/bin/bash"  
      ],  
      "icon": "terminal-bash"  
    }  
  },  
  "terminal.integrated.cursorBlinking": false,  
  "terminal.integrated.copyOnSelection": true,  
  "terminal.integrated.windowsEnableConpty": true,  
  // todo settings: language JAVASCRIPT  
  "javascript.validate.enable": true,  
  "javascript.autoClosingTags": false,  
  "javascript.updateImportsOnFileMove.enabled": "always",  
  // todo settings: language TYPESCRIPT  
  "typescript.validate.enable": true,  
  "typescript.autoClosingTags": false,  
  "typescript.updateImportsOnFileMove.enabled": "always",  
  // todo settings: extension Auto Rename Tag  
  "auto-rename-tag.activationOnLanguage": [  
    "html",  
    "xml",  
    "php",  
    "jsx"  
  ],  
  // todo settings: extension CSS, SCSS, SASS, LESS, STYLUS  
  "[sass]": {  
    "editor.colorDecorators": true  
  },  
  "scss.validate": false,  
  "css.validate": false,  
  "less.validate": false,  
  // todo settings: Linting  
  "editor.codeActionsOnSave": {  
    "source.fixAll.eslint": "explicit",  
    "source.fixAll.stylelint": "always"  
  },  
  "eslint.validate": [  
    "javascript",  
    "javascriptreact",  
    "typescript",  
    "typescriptreact"  
  ],  
  "stylelint.enable": true,  
  "stylelint.validate": [  
    "css",  
    "scss"  
  ],  
  // todo settings: extension BOOKMARKS  
  "bookmarks.navigateThroughAllFiles": false,  
  "bookmarks.saveBookmarksInProject": true,  
  "bookmarks.wrapNavigation": true,  
  // todo settings: extension Project manager  
  "projectManager.sortList": "Name",  
  "projectManager.groupList": true,  
  "projectManager.tags": [  
    "Personal useful",  
    "Personal learning",  
    "Personal example",  
    "Personal projects (BACK)",  
    "Personal projects (FRONT)",  
    "Personal projects (SERVER)",  
    "Personal projects (UTILS)",  
    "Github actions",  
    "Work (Slotegrator)",  
    "Work (Reliab Tech)",  
    "VSCode extension",  
    "Learning types",  
    "Different",  
    "Docker",  
    "Prototypes",  
    "Configurations",  
    "GO",  
    "PHP",  
    "Work (Golang Tech)"  
  ],  
  // todo settings: extension Indent Rainbow  
  "indentRainbow.colors": [  
    "rgba(51, 55, 72, 1.00)",  
    "rgba(51, 55, 72, 0.66)",  
    "rgba(51, 55, 72, 0.5)",  
    "rgba(51, 55, 72, 0.33)",  
    "rgba(51, 55, 72, 0.10)"  
  ],  
  // todo settings: extension Todo Tree  
  "todo-tree.general.tags": [  
    "TODO",  
    "FIXME",  
    "ERROR",  
    "INFO"  
  ],  
  "todo-tree.highlights.enabled": true,  
  // todo settings: extension Better Comments  
  "better-comments.highlightPlainText": false,  
  "better-comments.tags": [  
    {  
      "tag": "ERROR",  
      "color": "#FF2D00

",  
      "strikethrough": false,  
      "backgroundColor": "transparent",  
      "bold": true,  
      "italic": true  
    },  
    {  
      "tag": "FIXME",  
      "color": "#3498DB

",  
      "strikethrough": false,  
      "backgroundColor": "transparent",  
      "bold": true,  
      "italic": true  
    },  
    {  
      "tag": "TODO",  
      "color": "#FF8C00

",  
      "strikethrough": false,  
      "backgroundColor": "transparent",  
      "bold": true,  
      "italic": true  
    }  
  ],  
  // todo settings: GIT  
  "git.mergeEditor": true,  
  "git.autofetch": true,  
  "git.autofetchPeriod": 60,  
  "git.enableSmartCommit": true,  
  "git.rebaseWhenSync": true,  
  "git.inputValidationSubjectLength": 72,  
  "git.confirmSync": false,  
  // todo settings: extension Git Graph  
  "git-graph.defaultColumnVisibility": {  
    "Date": true,  
    "Author": true,  
    "Commit": true  
  },  
  "git-graph.commitDetailsView.autoCenter": false,  
  "git-graph.commitDetailsView.fileView.fileTree.compactFolders": true,  
  "git-graph.commitDetailsView.fileView.type": "File Tree",  
  "git-graph.commitDetailsView.location": "Docked to Bottom",  
  "git-graph.date.format": "ISO Date & Time",  
  "git-graph.graph.uncommittedChanges": "Open Circle at the Checked Out Commit",  
  "git-graph.referenceLabels.alignment": "Normal",  
  "git-graph.repository.commits.fetchAvatars": true,  
  "git-graph.repository.commits.showSignatureStatus": true,  
  "git-graph.repository.showStashes": false,  
  "git-graph.markdown": true,  
  "git-graph.tabIconColourTheme": "grey",  
  "git-graph.customBranchGlobPatterns": [  
    {  
      "name": "Feature Requests",  
      "glob": "heads/feature/*"  
    },  
    {  
      "name": "Bugfix Requests",  
      "glob": "heads/bugfix/*"  
    }  
  ],  
  // todo settings: extension Peacock  
  "peacock.favoriteColors": [  
    {  
      "name": "Angular Red",  
      "value": "#B52E31

"  
    },  
    {  
      "name": "Auth0 Orange",  
      "value": "#EB5424

"  
    },  
    {  
      "name": "Azure Blue",  
      "value": "#007FFF

"  
    },  
    {  
      "name": "C# Purple",  
      "value": "#68217A

"  
    },  
    {  
      "name": "Gatsby Purple",  
      "value": "#639"  
    },  
    {  
      "name": "Go Cyan",  
      "value": "#5DC9E2

"  
    },  
    {  
      "name": "Java Blue-Gray",  
      "value": "#557C9B

"  
    },  
    {  
      "name": "JavaScript Yellow",  
      "value": "#F9E64F

"  
    },  
    {  
      "name": "Mandalorian Blue",  
      "value": "#1857A4

"  
    },  
    {  
      "name": "Node Green",  
      "value": "#215732

"  
    },  
    {  
      "name": "React Blue",  
      "value": "#00B3E6

"  
    },  
    {  
      "name": "Something Different",  
      "value": "#832561

"  
    },  
    {  
      "name": "Vue Green",  
      "value": "#42B883

"  
    }  
  ],  
  // todo settings: extension Code-runner  
  "code-runner.executorMap": {  
    "typescript": "node_modules/.bin/ts-node"  
  },  
  "code-runner.saveFileBeforeRun": true,  
  // todo settings: extension Prettier  
  // "editor.defaultFormatter": "esbenp.prettier-vscode",  
  // "editor.formatOnSave": true,  
  // todo settings: extension Git Stash  
  "gitstash.explorer.itemDisplayMode": "show-empty",  
  "gitstash.explorer.items.repository.tooltipContent": "${path}\n└─ ${name} (${stashesCount})",  
  "gitstash.explorer.items.stash.labelContent": "#${index} - ${branch}",  
  "gitstash.explorer.items.stash.descriptionContent": "${ago}",  
  "gitstash.explorer.items.file.decoration": "badge-color",  
  "gitstash.explorer.items.file.icons": "file",  
  // todo settings: extension Run in Termianl  
  "runInTerminal.clearBeforeRun": true,  
  // todo settings: extension Auto Close Tag  
  "auto-close-tag.enableAutoCloseTag": true,  
  "auto-close-tag.enableAutoCloseSelfClosingTag": true,  
  "auto-close-tag.SublimeText3Mode": true,  
  "auto-close-tag.insertSpaceBeforeSelfClosingTag": false,  
  "auto-close-tag.fullMode": false,  
  "auto-close-tag.disableOnLanguage": [  
    "javascript",  
    "typescript"  
  ],  
  // todo settings: extension PHP Server  
  "phpserver.browser": "google-chrome",  
  "phpserver.autoOpenOnReload": false,  
  "phpserver.relativePath": "server",  
  // todo settings: Inlay Hints  
  "editor.suggest.preview": true,  
  "editor.inlayHints.enabled": "on",  
  "editor.inlayHints.fontFamily": "JetBrains Mono, Hack, monospace",  
  "editor.inlayHints.fontSize": 14,  
  "editor.inlayHints.padding": true,  
  "javascript.inlayHints.enumMemberValues.enabled": true,  
  "javascript.inlayHints.functionLikeReturnTypes.enabled": true,  
  "javascript.inlayHints.parameterNames.enabled": "all",  
  "javascript.inlayHints.parameterTypes.enabled": true,  
  "javascript.inlayHints.propertyDeclarationTypes.enabled": true,  
  "javascript.inlayHints.variableTypes.enabled": true,  
  "typescript.inlayHints.enumMemberValues.enabled": true,  
  "typescript.inlayHints.parameterTypes.enabled": true,  
  "typescript.inlayHints.propertyDeclarationTypes.enabled": true,  
  "typescript.inlayHints.functionLikeReturnTypes.enabled": true,  
  "typescript.inlayHints.variableTypes.suppressWhenTypeMatchesName": true,  
  "typescript.inlayHints.parameterNames.suppressWhenArgumentMatchesName": true,  
  "typescript.inlayHints.variableTypes.enabled": true,  
  "workbench.colorCustomizations": {  
    "editorInlayHint.background": "#6497b9d4",  
    "editorInlayHint.foreground": "#331818

",  
    "editorInlayHint.typeBackground": "#6497b9d4",  
    "editorInlayHint.typeForeground": "#331818

"  
  },
  // todo settings: File Nesting  
  "explorer.fileNesting.enabled": true,  
  "explorer.fileNesting.patterns": {  
    "package.json": "package-lock.json, yarn.lock, .stylelintrc, .stylelintrc.js, .eslintrc, .prettierrc, .eslintrc.json, .eslintrc.js, .editorconfig, babel.config.js, vue.config.js, .browserslistrc, nest-cli.json, .eslintrc.cjs, nodemon.json, .stylelintrc.json",  
    ".gitignore": ".stylelintignore, .eslintignore, .dockerignore, .prettierignore, .vscodeignore, .npmignore",  
    ".eslintignore": ".prettierignore",  
    "tsconfig.json": "tsconfig.build.json, tsconfig-checks.json, jsconfig.json, tsconfig.node.json",  
    "readme.md": "license"  
  },  
  "explorer.fileNesting.expand": false,  
  // todo settings: Dimmer Block  
  "dimmer.enabled": true,  
  "dimmer.opacity": 80,  
  "dimmer.delay": 10,  
  // todo settings: Git lens  
  "gitlens.blame.compact": true,  
  "gitlens.blame.ignoreWhitespace": true,  
  "gitlens.blame.format": "${author|15} ${agoOrDate|14-}",  
  "gitlens.views.stashes.files.compact": true,  
  "gitlens.views.stashes.files.layout": "tree",  
  "gitlens.views.formats.stashes.label": "${message|20} ${ago} (${changesShort})",  
  // todo settings: OTHER  
  "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",  
  "debug.onTaskErrors": "abort",  
  "security.workspace.trust.untrustedFiles": "open",  
  "files.autoSave": "onFocusChange",  
  "editor.unicodeHighlight.ambiguousCharacters": false,  
  "git.ignoreRebaseWarning": true,  
  "workbench.editor.empty.hint": "hidden",  
  "git.replaceTagsWhenPull": true,  
  "prettier.enable": true,  
  "git.openRepositoryInParentFolders": "never",  
  "editor.unicodeHighlight.invisibleCharacters": false,  
  "[markdown]": {  
    "editor.defaultFormatter": "DavidAnson.vscode-markdownlint"  
  },  
  "[php]": {  
    "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"  
  },  
  "[json]": {  
    "editor.defaultFormatter": "rvest.vs-code-prettier-eslint"  
  }  
}
```