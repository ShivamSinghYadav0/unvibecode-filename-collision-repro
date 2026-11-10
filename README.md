# UnvibeCode Filename Collision Reproduction

## Problem
UnvibeCode 0.4.0 generates the same download filename
for two different source file paths.

## Test Environment
- UnvibeCode: 0.4.0
- Python: 3.14.0
- OS: Windows
- Test repository: 3 Python source files

## Steps to Reproduce
1. Clone this repository.
2. Install UnvibeCode:
   py -m pip install unvibecode==0.4.0
3. Run:
   py -m unvibecode review --repository .
4. Open the generated Connected Code Map.
5. Select api/user_service.py.
6. Download its Optimal connection context.
7. Repeat for api_user_service.py.
8. Compare downloaded filenames and JSON contents.

## Expected
Each source file should have a distinct download filename.

## Actual
Both downloads use the same base filename:

api_user_service.py_optimal_connection_context_for_llm.json

The browser may append (1) to avoid overwriting an
existing download.

The JSON contents correctly identify different
selected_file paths.

## Impact
Flattening source paths into download filenames creates
collisions. This makes automated file identification
ambiguous and may cause overwrites in workflows that do
not rename duplicate downloads.

## Status
Reproduced using UnvibeCode 0.4.0.
