
# matlab-starter

This project aims to fix the rendering problems matlab experience on linux installs.
This is done by:

- 1. Swaping matlab's local libstdc++ file with system libstdc++.
- 2. Set some java options before starting matlab.

The solution are derived from: [matlab-discussion](https://in.mathworks.com/matlabcentral/answers/1631110-when-launching-matlab-i-get-the-following-error-mesa-loader-failed-to-open-iris)

## Swap libstdc++

To swap libstdc++ simply execute:

```bash
MATLAB_ROOT=/usr/local/MATLAB/R2024a
cd $MATLAB_ROOT/sys/os/glnx64
mv libstdc++.so.6 libstdc++.so.6.bak
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 .
```

Change `$MATLAB_ROOT` to the correct path if matlab is not installed on the
default location. The path to libstdc++ may also be be different on different
distros.

## Starting matlab

After changing the libstdc++ driver, matlab can be started without rendering
problems by opening matlab form a directory which includes the provided `java.opts`
file

The `start-matlab` provides a dynamic way to solve this by changing directory to
somewhere the `java.opts` file exists before starting matlab. To use the script
copy the `java.opts` to `$HOME/.config/matlab` or change the `$config_path`
inside the script. If `matlab` is not in path the variable, `$matlab_exec`, can
be changed to the matlab executable.

## NB!

This is no official solution, use the information provided in this repo at your
own risk.
