PVM
===
PVM��һ��PHP�ű����棬����Э�����PHPһ�仰webshell��

���������PHP 5.3.3�޸Ķ��������ܲ�����Ҫ������ģ����ɣ�

һ����PHP��չpwatch��ext/pwatch/������webserver�ڼ��ӹؼ��������ã�eval�ȣ���һ���йؼ��������ã����GET/POST/COOKIE���������ݷ��͸�pvmģ��ִ�С�

һ��SAPI�ӿ�pvm��sapi/pvm/������Ϊ�����򣬸������GET/POST/COOKIE���������ݣ�������Zend����ִ�У�ͨ�������۵�׷�ٵķ�ʽ�ж��Ƿ����ⲿ��������ؼ�������eval�ȣ���
linux����
---------
����pwatch

cd ext/pwatch/

phpize

./configure

make

����ext/pwatch/modules/pwatch.so

����pvm

make

����sapi/pvm/pvm


win����
-------
require:

	VC 2008 SP1
	
	php-sdk-binary-tools-20110915.zip
	
	deps-5.3-vc9-x86.7z
	
step:

	unzip php-sdk-binary-tools-20110915.zip to php-sdk
	
	run bin\phpsdk_setvars.bat and bin\phpsdk_buildtree.bat phpdev in "Visual Studio 2008 Command Prompt"
	
	unzip deps-5.3-vc9-x86.7z to php-sdk\phpdev\vc9\x86\
	
	copy php-5.3.3 source code dir to php-sdk\phpdev\vc11\x86\php-5.5.3-src\
	
	run buildconf in php-sdk\phpdev\vc11\x86\php-5.5.3-src\
	
	configure --disable-zts
	
	nmake
	
	����Release\pvm.exe
	
��װpwatch
-----------
�༭php.ini������pwatch��չ:extension=/path/to/pwatch.so
	
�÷�
-----
sapi/pvm/pvm [-g <GETSTRING>] [-p <POSTSTRING>] [-i <POSTDATAFILE>] [-k <COOKIESTRING>] [-t <METHODSTRING>] [-l <logfile>] [-f <file>]

  -d               decode POST data		����POST���ݣ���\xAA\xBB����ʽ���룬���ⲻ�ɼ��ַ�
  
  -g <querystring> GET data						QUERYSTRING����
 
  -p <postdata>    POST data					POST����
 
  -i <postdatafile>POST data file			POST�����ļ�

  -k <cookies>     COOKIE data				COOKIE����

  -t <method>      METHOD(GET\POST)		���󷽷���GET��POST

  -l <logfile>     log to file				�Ѽ��ӽ��������ļ�

  -f <file>        Parse <file>				Ҫִ�е���php�ű�

Release\pvm.exe -g c=d -p a=b -k e=f -t POST -f testscripts\11.php
	
��ʾ��Warning: eval(): Eval code contains data that might be tainted in E:\PHP\php-5.3.3\testscripts\11.php on line 1
	
֤����php�ļ�������һ�仰ľ��