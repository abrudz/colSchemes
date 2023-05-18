# Automated Colour Scheme Import/Export for Dyalog's Windows IDE

Dyalog's Windows IDE stores colour schemes as binary blobs in the registry, making it awkward to share colour schemes with others.

This tool makes it simple instead:

1. Place the repository inside `%USERPROFILE%\Documents\Dyalog APL Files\StartupSession` so you get a folder called e.g. `C:\Users\JDoe\Documents\Dyalog APL Files\StartupSession\colSchemes`.

2. On version 18.2 or earlier only (19.0+ does not need this), in the above folder, create a new file `polyfillRun.apln`  containing:<pre>:Namespace polyfillRun<br>    ##.Run⍬<br>:EndNamespace</pre>

3. Start Dyalog and close it again.

4. You now have a folder at `%USERPROFILE%\Documents\Dyalog APL {version} Files\colSchemes` (e.g. `C:\Users\JDoe\Documents\Dyalog APL-64 19.0 Unicode Files\colSchemes`) with Dyalog Colour Scheme files (.dcs). You can share such files with others, or drop their Dyalog Colour Scheme files into your folder.

### Notes

* The above installation makes colSchemes available from all versions of Dyalog. To install for a specific version only, put in the corresponding version's StartupSession folder, e.g. `C:\Users\JDoe\Documents\Dyalog APL-64 19.0 Unicode Files\StartupSession`.

* Dyalog will import all schemes every time it starts, and will export all schemes every time it closes.

* You can also manually import and export schemes from inside Dyalog with `⎕SE.colSchemes.Import 0` and `⎕SE.colSchemes.Export 0`.

* You can selectively import and export schemes using a regex as left argument to these functions. E.g. `'^My' ⎕SE.colSchemes.Export 0` will only export schemes that begin with "My".

* Changing the `0` to a `1` imports and exports from the version-agnostic folder rather than the version-specific folder.

* Alternatively, you can give a custom folder path instead of the `0` or `1`.

* The .dcs files are plain-text files, so you can safely send their contents in emails and via various messaging services. You could also experiment with creating your own editor for them…
