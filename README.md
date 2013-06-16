## Usage

Just put `upx.exe` and `upx.py` into your main folder and change your `build.py` file a little bit:

    import sys
    
    from distutils.core import setup
    from upx import UPXPy2exe
    
    sys.argv.append('py2exe')
    
    setup(
        cmdclass = {'py2exe': UPXPy2exe},
        options = {
            'py2exe': {
                'verbose': True,
                'bundle_files': 1,   # Makes a single EXE file
                'compressed': True,
                'upx': True,
                'upx_options': '--best --lzma',
                'upx_excludes': [],  # Excludes libraries from being compressed with UPX
                'dll_excludes': ['MSVCP90.dll', 'HID.DLL', 'w9xpopen.exe']
            }
        },
        windows = [{'script': 'main.py'}],  # The name of your main script file
        zipfile = None
    )