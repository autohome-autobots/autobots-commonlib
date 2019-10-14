# autobots-commonlib
汽车人开发框架说明文档
# RN开发框架说明





## 组件

### Nav
> 使用导航器可以让你在应用的不同场景（页面）间进行切换。导航器通过路由对象来分辨不同的场景。  
 

#### 调用方式
``` javascript
  import {Nav} from 'autobots-commonlib';
  import HomePage from './pages/HomePage';
  
  Nav.pop();//返回上一页面
  
  //跳转至页面
  Nav.push({
              name: 'HomePage', 
              component: HomePage,
              params: {
              }
        });
  //你也可以调用Nav.navigator对象来使用RN的完整路由功能
  Nav.navigator.popToTop()
  ...
  //更多可查看RN帮助文档
```

### Native
> 提供RN与原生交互功能。  
 
#### 调用方式
``` javascript
  import {Native} from 'autobots-
  ';
  //回到汽车人首页
  Native.gotoHomePage();
  
  //获取动态口令
  Native.getVerCode(cb);
    cb为回调函数
  
  //获取员工OA账号
  Native.getEmpCode();
  
  //...后续回有更多接口加入
   
```

### Http
> 通用网络请求。  
 
#### 调用方式
``` javascript
import {Http} from 'autobots-commonlib';
  
Http.request("http://xxx.com",{name:""}).then(function(data){
          if(data)
          {
	          //成功
	          ...
          }else
          {
	          //失败
	          ...
          }
      });

   
```


### Components
> 包含一些基础RN组件。  
 
#### Navbar
``` javascript
  import {Components} from 'autobots-commonlib';
  const {Navbar} = Components;
  
  ...
  render(){
	return(<Navbar title="xxx" onLeftButtonPress={()=>{
		  //左侧返回按钮点击事件
          ...
      }}  />)
  }
  ...
   
```

#### ImagesPicker
``` javascript
  import {Components} from 'autobots-commonlib';
  const {ImagesPicker} = Components;
  
  ...
  <ImagesPicker ref={imgPicker=>this.imgPicker=imgPicker} onPicked={(data)=>{
		   //返回值
			  单选返回图片url
			  多选返回图片url数组
 }} />

 this.imgPicker.MutiPick(); //多选
 this.imgPicker.SinglePick(); //单选
 ...
   
```


#### CameraPicker
``` javascript
  import {Components} from 'autobots-commonlib';
  const {CameraPicker} = Components;
  
  ...
  <CameraPicker ref={caPicker=>this.caPicker=caPicker} onPicked={(data)=>{
		   //返回值
		   返回图片url
 }} />

 this.caPicker.Pick(); //拍照


 ...
   
```

#### EmployeePicker
``` javascript
  import {Components} from 'autobots-commonlib';
  const {EmployeePicker} = Components;
  
  ...
  <EmployeePicker ref={empPicker=>this.empPicker=empPicker} onPicked={(data)=>{
		   //返回值
		   返回图片url
 }} />

 this.empPicker.MutiPick("选择出差人","最近选择出差人"); //多选
 this.empPicker.SinglePick("选择出差人","最近选择出差人");//单选

 ...
   
```

#### Loading
> 调用汽车人统一loading。  

``` javascript
  import {Components} from 'autobots-commonlib';
  const {MainLoading} = Components;
  //短文本
  MainLoading.Show();
  //超长文本
  MainLoading.ShowLong();

```

### Config
> 提供系统内的一些配置参数。  
 
#### 调用方式
``` javascript
  import {Config} from 'autobots-commonlib';
  //获取参数对象
  var c = Config.get();
  
  console.log(c);
  //输出结果
   {
	  name:"xxx",
	  homeTitle:"xxx", 
	  startApp:object,//首页对象
	  employee:{empCode:"xxx",empName:"xxx"},//当前登录人信息	
	  urlParams:"xxx",//从原生获取的网页传递参数
	}
   
```

### Toast
> toast功能。  
 
#### 调用方式
``` javascript
  import {Toast} from 'autobots-commonlib';
  //短文本
  Toast.Show('xxx');
  //超长文本
  Toast.ShowLong('xxx');

```

### Alipay
> 支付宝支付功能，如买健身劵功能会用到。
``` javascript
  import {Alipay} from 'autobots-commonlib';
  
  Alipay.pay(data,callback)
  data 包含订单信息之类支付数据
  callback 回调函数
  
```

### WXPay
> 微信支付功能，如买健身劵功能会用到。
``` javascript
  import {WXPay} from 'autobots-commonlib';
  
  WXPay.pay(data,callback)
  data 包含订单信息之类支付数据
  callback 回调函数
  
```

### Scan
> 调用二维码扫描。
``` javascript
  import {Scan} from 'autobots-commonlib';
  
  Scan.start(callback)
  callback 回调函数
  
```

### DingDing
> 分享到钉钉功能。
``` javascript
  import {DingDing} from 'autobots-commonlib';
  
  DingDing.shareText(content,callback)
  content为分享的内容，callback为回调函数
  
  DingDing.shareUrl(title,url,pic,content,callback)
  title为标题，url为分享的URL，pic为图片，content为分享的内容，callback为回调函数
  
  DingDing.sharePic(pic,callback)
  pic为分享的图片，callback为回调函数
  
```

### WXShare
> 分享到微信功能。
``` javascript
  import {WXShare} from 'autobots-commonlib';
  
  WXShare.shareText(content,wxtype,callback)
  content为分享的内容，wxtype为 1表示微信，2表示朋友圈，callback为回调函数
  
  WXShare.shareUrl(title,url,pic,content,wxtype,callback)
  title为标题，url为分享的URL，pic为图片，content为分享的内容，wxtype为 1表示微信，2表示朋友圈，callback为回调函数
  
  WXShare.sharePic(pic,wxtype,callback)
  pic为分享的图片，wxtype为 1表示微信，2表示朋友圈，callback为回调函数
  
```

### Update
> 检测升级。
``` javascript
  import {Update} from 'autobots-commonlib';
  
  Update.Open(callback)
  callback为回调函数
  
```

### JumpToFeedback
> 跳转到意见反馈界面。
``` javascript
  import {JumpToFeedback} from 'autobots-commonlib';
  
  JumpToFeedback.Open(callback)
  callback为回调函数
  
```

### Vpn
> 跳转到意见反馈界面。
``` javascript
  import {Vpn} from 'autobots-commonlib';
  
  Vpn.connectVpn(username,password,serverAddress,sharedSecret,remoteId,localId,preferenceTitle)
  连接Vpn
  
  Vpn.disconnectVpn()
  断开Vpn连接
  
  Vpn.getVpnStatus(callback)
  得到Vpn的状态
  
```

### AutoLinkVPN
> 自动连接Vpn功能。
``` javascript
  import {AutoLinkVPN} from 'autobots-commonlib';
  
  AutoLinkVPN.addListener(handler)
  添加监听
  
  AutoLinkVPN.removeListener(handler)
  断开监听
  
  AutoLinkVPN.removeAllListeners()
  断开所有监听
  
  #### 调用方式
  _handler = res => {
    // 处于内网或者vpn连接成功
    alert(res);
  }

  componentDidMount() {
    AutoLinkVPN.addListener(this._handler);
  }

  componentWillUnmount() {
    AutoLinkVPN.removeListener(this._handler);
  }
  
```

### NewAutobots
> 提供一些辅助函数。 
``` javascript

  //获取系统版本信息
  NewAutobots.getAppVersion(callback)
  如，
   _getAppVersion = () => {
    return new Promise((resolve, reject) => {
      if (NewAutobots) {
        NewAutobots.getAppVersion(function(result, data) {
          if (data) {
            resolve(data);
          } else {
            reject(new Error('data do not exist'));
          }
        });
      } else {
        reject(new Error('NewAutobots do not exist'));
      }
    })
      .then(res => [null, res])
      .catch(err => [err, null]);
  };
  
  //退出登录
  NewAutobots.logout(callback)
  如，
  NewAutobots.logout();
  
  //原生的退出方法
  NewAutobots.backPress(callback)
  如，
  NewAutobots.backPress();
  
  //设置pin码间隔的时间保存到原生端，单位为分钟
  NewAutobots.setPinLockFrequency(minute,callback)
  如，
	  const minute = data.hours * 60;
	// 存RN本地
	global.storage.save({
	  key: 'newautobots-mine-pinFrequency',
	  data: minute
	});
	// 存原生
	NewAutobots.setPinLockFrequency(minute);

```
