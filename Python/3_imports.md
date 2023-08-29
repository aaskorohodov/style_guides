# Table of contents

<!-- TOC -->
* [Table of contents](#table-of-contents)
* [Imports in document's structure](#imports-in-documents-structure)
* [Imports order](#imports-order)
* [Circular imports](#circular-imports)
<!-- TOC -->

# Imports in document's structure

- Imports should be put on top of the file, except for cases, when such import breaks the code

There can be rare cases, where import themselves can trigger some unwanted cascade of code-flow, that must be done
only after something else. This is a clear indication of some sort of antipattern, and if fixing this is too 
complicated, imports can be done somewhere deeper in the code.

# Imports order

Imports should be organized this way:

1. future and annotations (this exact modules, ONLY if are required for type-checking)
2. 'Non-from' imports of third-party libraries
3. 'From' imports of third-party libraries
4. 'Non-from' imports from application
5. 'From' imports from application

Each import inside this block should be separated by 1 spacing. If file have a docstring, it should be on top,
higher than any imports.

```python
"""Docstring goes here"""

from __future__ import annotations
from typing import TYPE_CHECKING

import third_party_library1
import third_party_library2

from third_party_library3 import module3
from third_party_library4 import module4

import this_app_module1
import this_app_module2

from this_app_module3 import my_module3
from this_app_module4 import my_module4
```

If some imports are made purely in purpose of type-annotating using TYPE_CHECKING, and are not used directly, 
such imports should go at the very end in all other imports (but still on top of the page). The inner order of the 
'if TYPE_CHECKING' block should be similar, as regular imports

```python
from typing import TYPE_CHECKING

import third_party_library1
import third_party_library2

from third_party_library3 import module3
from third_party_library4 import module4

import this_app_module1
import this_app_module2

from this_app_module3 import my_module3
from this_app_module4 import my_module4

if TYPE_CHECKING:
    import third_party_library3
    import third_party_library4

    from third_party_library5 import module5
    from third_party_library6 import module6

    import this_app_module1
    import this_app_module2

    from this_app_module1 import my_module1
    from this_app_module2 import my_module2
```

# Circular imports

If file_1.py have already imported a module named 'modul_1', and file_2.py have imported modul_2 from file_2.py, it is
considered a bad practice to import module_1 again in file_2.py. This is because while importing module_2 into 
file_2.py, you will already have all the imports from file_1.py. This means that you will import modul_1 twice for
no reason.

This can be controversial, because file_2.y will not have implicit import of module_1, that it uses. But still, 
consider using imports only once.