# Move to new file Nextjs issue

Affects typescript versions **5.5 and above**.

## How to reproduce

1. Open `src/next.ts` in this repo
2. Highlight the 3rd line (`const metadata: Metadata = {};`) in the file
3. Hit Cmd+. to open the refactoring context menu
4. Select "Move to a new file"

Note how the metadata constant is NOT moved to a new file.

## Counter example

Executing the reproduction above on the `src/react.ts` file works fine.

## TS Server Logs

```
Err 5265  [22:21:07.805] Exception on executing command {
  "seq": 1007,
  "type": "request",
  "command": "getEditsForRefactor",
  "arguments": {
    "file": "/Users/daniel/Code/move-to-new-file-repro/src/next.ts",
    "startLine": 3,
    "startOffset": 1,
    "endLine": 3,
    "endOffset": 31,
    "refactor": "Move to a new file",
    "action": "Move to a new file",
    "startPosition": 39,
    "endPosition": 69
  }
}:

    Debug Failure.

    Error: Debug Failure.
        at Object.addImportFromExportedSymbol (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:154243:32)
        at /Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:144288:19
        at Map.forEach (<anonymous>)
        at addTargetFileImports (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:144282:17)
        at getNewStatementsAndRemoveFromOldFile (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:143512:3)
        at doChange4 (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:144488:3)
        at /Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:144477:77
        at _ChangeTracker.with (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:174306:5)
        at Object.getRefactorEditsToMoveToNewFile [as getEditsForAction] (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:144477:60)
        at Object.getEditsForRefactor (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:142603:31)
        at Object.getEditsForRefactor2 [as getEditsForRefactor] (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:149939:32)
        at proxy.<computed> [as getEditsForRefactor] (/Users/daniel/.vscode/extensions/mxsdev.typescript-explorer-0.4.2/node_modules/@ts-type-explorer/typescript-plugin/dist/index.js:15:15)
        at IpcIOSession.getEditsForRefactor (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:191087:49)
        at getEditsForRefactor (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:189305:43)
        at /Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:191491:69
        at IpcIOSession.executeWithRequestId (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:191483:14)
        at IpcIOSession.executeCommand (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:191491:29)
        at IpcIOSession.onMessage (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/typescript.js:191533:51)
        at process.<anonymous> (/Users/daniel/Code/move-to-new-file-repro/node_modules/typescript/lib/tsserver.js:523:14)
        at process.emit (node:events:518:28)
        at emit (node:internal/child_process:950:14)
        at process.processTicksAndRejections (node:internal/process/task_queues:83:21)

File text of /Users/daniel/Code/move-to-new-file-repro/src/next.ts:
    import type { Metadata } from "next";

    const metadata: Metadata = {};

    export default metadata;
```
