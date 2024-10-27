
# matlab-starter

This project aims to fix the rendering problems matlab experience on linux installs.

To fix it, open a terminal an execute the following:

```bash
MATLAB_ROOT=/usr/local/MATLAB/R2024a
cd $MATLAB_ROOT/sys/os/glnx64
mv libstdc++.so.6 libstdc++.so.6.bak
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6 .
```

NB! The path to libstdc++ may be be different on different distros.

After this matlab can be started through the `start-matlab` script.

The solution are derived from: [matlab-discussion](https://in.mathworks.com/matlabcentral/answers/1631110-when-launching-matlab-i-get-the-following-error-mesa-loader-failed-to-open-iris)
