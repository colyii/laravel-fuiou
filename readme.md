Fuiou 富友金账户

安装

composer require colyii/laravel-fuiou dev-master

或者在composer.json中加入

 "require": {
	"colyii/laravel-fuiou": "dev-master"
}

更新依赖 composer update

使用说明

找到 config/app.php 文件

'providers' => [

   Colyii\Fuiou\FuiouServiceProvider::class,
]
运行 php artisan vendor:publish 命令

配置文件 config/colyii-fuiou.php 已经生成，按照要求配置即可

DEMO

PC 查询余额

$fuiou   = app('PcFuiou');
$params = [
	'cust_no' => '18672385088',
];
$balance = $fuiou->balanceAction($params);

=============================================

Mobile 开户
$fuiou = app('MobileFuiou');
$params = [
    *** //app 页面开户参数
];
$rsaSign = $fuiou->rsaSign($params, 'app/appWebReg');
$balance = $fuiou->appWebReg($params, $rsaSign);