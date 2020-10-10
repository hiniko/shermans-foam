# Logging

I can't keep this in my head for some reason:

- `UE_LOG(LogTemp, Warning, TEXT("We %s hit %s"), *actor_name, *our_name);`
    - `LogTemp` and `Warning` are the Category  and Verbosity Mask. See engine source `Engine\Source\Runtime\Core\Public\Logging\LogVerbosity.h` for listings
    - The text portion can use `printf` specifiers 
    - when passing `FString`, remember to dereference them so the log can use the underlaying `TCHAR`, 