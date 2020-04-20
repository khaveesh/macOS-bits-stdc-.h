# macOS <bits/stdc++.h>

## Support for &lt;bits/stdc++.h> in macOS\*\*

macOS ships by default with the LLVM/Clang compiler which does not support GNU/GCC extensions such as the bits/stdc++.h header file that every beginner tends to use in their C++ code.

This is a problem even when you use g++ in macOS, as Apple use g++ as a frontend to clang++ for legacy reasons.

## Solution

1. You need to create a directory 'bits' under the folder /usr/local/include.
   This can be done by opening Terminal and running the following commands:

    ```fish
    mkdir /usr/local/include
    ```

2. You need to copy the contents of the [stdc++.h](../blob/master/stdc++.h) included in this repository into the newly created bits folder:

    ```fish
    curl https://raw.githubusercontent.com/khaveesh/macOS-bits-stdc-.h/master/stdc%2B%2B.h > /usr/local/include/bits/stdc++.h
    ```

3. Profit! You can now write:

    ```fish
    #include <bits/stdc++.h>`
    ```

## Recommendation

There is a reason why Clang and even Microsoft do not include this file in their compilers. **It is a really bad coding practice**.

### Explanation

bits/stdc++.h is a non-standard header file containing a list of **_all_** header files available. Everyone who has written atleast a moderately complex program in C++ know how much of a pain-in-the-a\*\* it is to find the appropriate header file for all the builtins used. So it is an easier way out to just include this bits/stdc++.h. But this means that all header files regardless of whether you're using them or not, are included in your code. This increases the compilation time of your code. This is especially noticeable in Competetive Programming where coders usually change one or two lines at max and frequently compile when debugging. Thus this delay in compilation adds up. So it is better to spend some time to know which functions you're using and include only the minimum required header files.

## TLDR

Copy and paste the following commands in your Mac terminal:

```fish
mkdir /usr/local/include
```

```fish
curl https://raw.githubusercontent.com/khaveesh/macOS-bits-stdc-.h/master/stdc%2B%2B.h > /usr/local/include/bits/stdc++.h
```

**But this is bad coding practice and you should consider this as a stopgap solution only and refrain from using this.**

## Source

The stdc++.h file is created from the **latest** stdc++.h file in the [GCC git repository](https://raw.githubusercontent.com/gcc-mirror/gcc/master/libstdc%2B%2B-v3/include/precompiled/stdc%2B%2B.h) with the non-Mac include directives removed.

## License: GPLv3

**Fun Fact**: This license was one of the primary reasons why Apple decided to fund the fledgling LLVM Compiler team in the University of Illinois. Read [Apple's Great GPL Purge](http://meta.ath0.com/2012/02/05/apples-great-gpl-purge/) to know more.
