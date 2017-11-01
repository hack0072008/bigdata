# big_data

## 参考
* http://blog.csdn.net/kkk584520/article/details/51476816#pip-安装
* http://blog.csdn.net/helei001/article/details/51285951
* http://blog.csdn.net/xueyingxue001/article/details/67634174



## 源码安装：
[安装bazel](https://docs.bazel.build/versions/master/install-redhat.html)
* 加源
* yum install bazel

[编译tensorflow](http://blog.csdn.net/kkk584520/article/details/51476816#安装-tensorflow)
* yum install patch

* pip install numpy

* cd tensorflow_src
* ./configure

* build
  CPU:bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
  GPU:bazel build -c opt --config=cuda //tensorflow/tools/pip_package:build_pip_package
* package
  mkdir -p /tmp/tensorflow_pkg
  bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg

    注[解决错误：error: invalid command 'bdist_wheel'](http://www.cnblogs.com/BugQiang/archive/2015/08/22/4732991.html)
    i>
    pip install setuptools --upgrade
    or
    ii>
    python -m pip uninstall pip setuptools
    yum remove python-pip python-setuptools

    yum clean python-pip python-setuptools
    yum remove python-pip python-setuptools

    yum install python-pip python-setuptools
    pip install --upgrade pip
         
* install
  pip install /tmp/tensorflow_pkg/tensorflow-x.x.x-py2-none-linux_x86_64.whl
* test
  python
  import tensorflow as tf
