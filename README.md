## 使用方式
#### composer引用
```
composer require kscsdk/ksyun_sdk
```
#### ak|sk配置
>获取到用户的aksk后配置在文件
```
~\.ksyun\config
```
>增加配置文件路径定义
```php
// 配置文件路径 
define('KSYUN_CONFIG_DIR', '');
$configFile = KSYUN_CONFIG_DIR . '/config';
```
#### config文件结构
```
{
    "ak":"your ak",
    "sk":"your sk"
}
```

## 功能列表
- [IAM](https://docs.ksyun.com/documents/1376)
- [KEC](https://docs.ksyun.com/documents/695)
- [EIP](https://docs.ksyun.com/documents/670)
- [VPC](https://docs.ksyun.com/products/3)
- [SLB](https://docs.ksyun.com/documents/1126)
- [CDN](https://docs.ksyun.com/read/latest/107/_book/index.html)
- [MONITOR](https://docs.ksyun.com/read/latest/81/_book/index.html)
- [TAG](https://docs.ksyun.com/read/latest/90/_book/index.html)

>敬请期待

## 推荐demo
```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Iam;
$response = Iam::getInstance()->request('ListUsers');
echo (string)$response->getBody();
```

```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Kec;
$response = Kec::getInstance()->request('DescribeInstances', [], 'cn-beijing-6');
echo (string)$response->getBody();
```

```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Eip;
$response = Eip::getInstance()->request('DescribeAddresses', ['query' => ['MaxResults' => 10]], 'cn-beijing-6');
echo (string)$response->getBody();
```

```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Iam;
$ak = 'this is ak';
$sk = 'this is sk';
$response = Iam::getInstance()->request('ListUsers', ['v4_credentials' => ['ak' => $ak, 'sk' => $sk]]);
echo (string)$response->getBody();
```

```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Cdn;   //详细CDN api调用示例 位于./tests/CdnTest.php
$response = Iam::getInstance()->request('GetCdnDomains', ['query'=>['DomainStatus' => 'online', 'CdnType' => 'download']);
echo (string)$response->getBody();
```

```
<?php
require('./vendor/autoload.php');
use Ksyun\Service\Monitor;   //详细Monitor api调用示例 位于./tests/MonitorTest.php
$response = Monitor::getInstance()->request('ListMetrics', ['query'=['Namespace' => 'KEC', 'InstanceID' => '7af8d721-fb03-4d5b-a4a7-0ff983a2c30b', 'PageIndex' => 1]], 'cn-beijing-6'); 
echo (string)$response->getBody();
```
