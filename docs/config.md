# 项目配置

项目配置存放于项目根目录下 `config` 目录中，包含三个文件

- `index.js` 是通用配置
- `dev.js` 是项目预览时的配置
- `prod.js` 是项目打包时的配置

## index.js —— 通用配置

```javascript
const config = {
  // 项目名称
  projectName: 'kj',
  // 项目创建日期
  date: '2018-6-8',
  // 设计稿尺寸
  designWidth: 750,
  // 项目源码目录
  sourceRoot: 'src',
  // 项目产出目录
  outputRoot: 'dist',
  // 通用插件配置
  plugins: {
    babel: {
      sourceMap: true,
      presets: ['env'],
      plugins: ['transform-class-properties', 'transform-decorators-legacy', 'transform-object-rest-spread']
    }
  },
  // 全局变量设置
  defineConstants: {},
  // 小程序端专用配置
  weapp: {},
  // H5 端专用配置
  h5: {
    publicPath: '/',
    staticDirectory: 'static',
    module: {
      postcss: {
        autoprefixer: {
          enable: true
        }
      }
    },
    // 自定义webpack配置
    webpack: {}
  }
};

module.exports = function(merge) {
  if (process.env.NODE_ENV === 'development') {
    return merge({}, config, require('./dev'));
  }
  return merge({}, config, require('./prod'));
};
```
