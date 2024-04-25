This repo breaks slither.

To Slither Team: Please clone this repo, run `foundryup` then `forge i`, then `forge build`, then `slither .` and you will get an output log of something similar to this:

`'forge clean' running (wd: /home/smartchain/code/audits/broken/slither-breaks/wallflower-contract-v2)
'forge build --build-info --skip */test/** */script/** --force' running (wd: /home/smartchain/code/audits/broken/slither-breaks/wallflower-contract-v2)
Traceback (most recent call last):
  File "/home/smartchain/.local/lib/python3.10/site-packages/slither/__main__.py", line 833, in main_impl
    ) = process_all(filename, args, detector_classes, printer_classes)
  File "/home/smartchain/.local/lib/python3.10/site-packages/slither/__main__.py", line 107, in process_all
    ) = process_single(compilation, args, detector_classes, printer_classes)
  File "/home/smartchain/.local/lib/python3.10/site-packages/slither/__main__.py", line 80, in process_single
    slither = Slither(target, ast_format=ast, **vars(args))
  File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slither.py", line 118, in __init__
    sol_parser.parse_top_level_items(ast, path)
  File "/home/smartchain/.local/lib/python3.10/site-packages/slither/solc_parsing/slither_compilation_unit_solc.py", line 351, in parse_top_level_items
    raise SlitherException(f"Top level {top_level_data[self.get_key()]} not supported")
slither.exceptions.SlitherException: Top level EventDefinition not supported
ERROR:root:Error:
ERROR:root:Top level EventDefinition not supported
ERROR:root:Please report an issue to https://github.com/crytic/slither/issues`
