# Flavour: Warn

This flavour builds on the toggle flavour and adds a third mode for PYTHON_LIST_FAILFAST.

| Value               | Behaviour                                                                 |
|---------------------|---------------------------------------------------------------------------|
| unset (or other)    | Error: RuntimeError on size change (fail-fast)                            |
| 0                   | Off: stock CPython behaviour, no check                                    |
| warn                | Stock behaviour, plus a RuntimeWarning at each size change                |

In warn mode the iterator keeps running as stock Python does, so elements can still be skipped,
but the program reports the change. The iterator then resynchronises its recorded size, so a
later change is reported again.

Example:

    PYTHON_LIST_FAILFAST=warn ./python demo_list.py

Change: Objects/listobject.c only. See flavour_warn.diff.

Status: not yet compiled or tested. Build and run the test suite before use.
