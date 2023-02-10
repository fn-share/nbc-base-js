nbc-base-js
--------------

Basic javascript library for NBC.

&nbsp;

## 关于本项目

本项目用于生成适用于浏览器环境的 nbc_base.js 库文件，这个库文件是 NBC 技术体系在网页端应用的基础依赖库。

下面将描述生成 `nbc_base.js`，以及生成压缩格式的 `nbc_base.min.js` 文件的操作过程。

&nbsp;

## 操作步骤

第一步，将本项目拉取到本地。

``` bash
git clone https://github.com/fn-share/nbc-base-js.git
```

第二步，安装依赖库。

``` bash
cd nbc-base-js
npm install
```

第三步，用 browserify 工具将库打包成 `nbc_base.js`

如果尚未安装 [browserify](https://github.com/browserify/browserify) 工具，请先执行如下命令：

``` bash
npm install browserify -g
```

然后打包，输出 `nbc_base.js` 。

``` bash
browserify -r create-hash -r create-hmac -r create-ecdh -r crypto-js -r safe-buffer -r bip32 -r tiny-secp256k1 -r bip66 -r base-x -r @subspace/vdf >nbc_base.js
```

第四步，将 `nbc_base.js` 压缩成 `nbc_base.min.js`

建议用 [UglifyJS](https://github.com/mishoo/UglifyJS) 实施压缩，如果尚未安该工具，请先执行如下命令：

``` bash
npm install uglify-js -g
```

然后启动压缩。

``` bash
uglifyjs nbc_base.js -c -m >nbc_base.min.js
```

&nbsp;

## 关于基础库

nbc_base 库打包了 `crypto-js, bip32, safe-buffer, @subspace/vdf` 等基础库，涉及 AES 加解密、hmac 算法、hash 算法、secp256k1 椭圆曲线算法、HD wallet 账号衍生算法、vdf 算法等，部分基础库我们未采用最新版本，因为最新版本塞入过多我们并不想要的代码。

按上述步骤打包后，最终得到的 `nbc_base.min.js` 尺寸是 629k 字节。

&nbsp;
