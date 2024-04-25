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

UPDATE: I upgraded to 0.10.1 using python3 -m pip install slither-analyzer -U but now I recieve this error:

`$ slither .
'forge clean' running (wd: /home/smartchain/code/audits/broken/slither-breaks/wallflower-contract-v2)
'forge config --json' running
'forge build --build-info --skip /test/* /script/* --force' running (wd: /home/smartchain/code/audits/broken/slither-breaks/wallflower-contract-v2)
ERROR:SlitherSolcParsing:
Failed to convert IR to SSA for Initializable contract. Please open an issue https://github.com/crytic/slither/issues.

Traceback (most recent call last):
File "/home/smartchain/.local/bin/slither", line 8, in
sys.exit(main())
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/main.py", line 753, in main
main_impl(all_detector_classes=detectors, all_printer_classes=printers)
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/main.py", line 859, in main_impl
) = process_all(filename, args, detector_classes, printer_classes)
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/main.py", line 107, in process_all
) = process_single(compilation, args, detector_classes, printer_classes)
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/main.py", line 80, in process_single
slither = Slither(target, ast_format=ast, **vars(args))
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slither.py", line 199, in init
self._init_parsing_and_analyses(kwargs.get("skip_analyze", False))
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slither.py", line 219, in _init_parsing_and_analyses
raise e
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slither.py", line 215, in _init_parsing_and_analyses
parser.analyze_contracts()
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/solc_parsing/slither_compilation_unit_solc.py", line 593, in analyze_contracts
self._convert_to_slithir()
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/solc_parsing/slither_compilation_unit_solc.py", line 834, in _convert_to_slithir
raise e
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/solc_parsing/slither_compilation_unit_solc.py", line 829, in _convert_to_slithir
contract.convert_expression_to_slithir_ssa()
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/core/declarations/contract.py", line 1579, in convert_expression_to_slithir_ssa
func.generate_slithir_ssa(all_ssa_state_variables_instances)
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/core/declarations/function_contract.py", line 140, in generate_slithir_ssa
add_ssa_ir(self, all_ssa_state_variables_instances)
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 206, in add_ssa_ir
fix_phi_rvalues_and_storage_ref(
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 526, in fix_phi_rvalues_and_storage_ref
fix_phi_rvalues_and_storage_ref(
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 526, in fix_phi_rvalues_and_storage_ref
fix_phi_rvalues_and_storage_ref(
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 526, in fix_phi_rvalues_and_storage_ref
fix_phi_rvalues_and_storage_ref(
[Previous line repeated 4 more times]
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 496, in fix_phi_rvalues_and_storage_ref
variables = [
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 497, in
last_name(dst, ir.lvalue, init_local_variables_instances) for dst in ir.nodes
File "/home/smartchain/.local/lib/python3.10/site-packages/slither/slithir/utils/ssa.py", line 363, in last_name
assert candidates
AssertionError`
