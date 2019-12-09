# - �ֶ����밲װ�������ã�������������ϵͳ -


## 1. **linux**

* �汾�ţ�Ubuntu 18.04
---

## 2. **Nginx**

  ��1���������Դ

  ```
 sudo apt-get update
  ```
  ![nginx](./pictures/nginx.png)
  
  ��2����װnginx
  ```
  sudo apt-get install nginx
  ```
   ![nginx2](./pictures/nginx2.png) 
  
  ��3����������ļ��Ƿ���ȷ&&����nginx
  
   ��������ļ��Ƿ���ȷ��
  ```
  nginx -t
  ```
  ![nginx6](./pictures/nginx6.png)
  
  ---
  **���׳��ֵ�����**���������root�û��£�����ʾ
  permission denied �� ��������Ҫ�л���root�û��Ի�ȡȨ��

---
  �����ļ���
  ```
  sudo vi /etc/nginx/nginx.conf
  ��user www.data��Ϊuser root
  ```
  ![nginx8](./pictures/nginx8.png)

  ---
  /etc/nginx �µ������ļ��ṹ
  ![nginx9](./pictures/nginx9.png)

  ��4������nginx����
   ```
    sudo /etc/init.d/nginx start
   ```
   ![nginx3](./pictures/nginx3.png)

  ��5�����������nginx����
  �������������localhost
  ![nginx4](./pictures/nginx4.png)

  ��6����������
  ![nginx5](./pictures/nginx5.png)

  ---

  
## 3. **Mysql**
 ��1�����ȼ��ϵͳ���Ƿ�װ��mysql
  ```
  sudo netstart -tap|grep mysql
  ```
  û�з�Ӧ��û����ʾ�Ѱ�װ���

   ��2����װmysql
   ```
   sudo apt-get install mysqp-server mysql-server
   ```
   ![mysql1](./pictures/mysql1.png)

   ---
   **�������** ��E���޷������ /var/lib/dpkg/lock-fronted(11: ��Դ������)

   **����ԭ��** ����ubuntuϵͳ��termial�£���apt-get install ��װ�����ʱ�������δ������ص�����½�terminal close����ʱ apt-get���̿���û�н��������������ٴ�����apt-get install ���װ��񣬿��ܻᷢ���������ʾ��
 
 �޷������ /var/lib/dpkg/lock - open (11: ��Դ��ʱ������)
�޷���������Ŀ¼(/var/lib/dpkg/)���Ƿ�������������ռ������


   **������** ��
   ```
   ps -aux
   ```
   �ҵ�����apt-get�Ľ���id��
   ```
   sudo kill id
   ```
   ���⼴�ɽ��

---
 �ٴ�ִ�������İ�װ����ָ��
 ![mysql2](./pictures/mysql2.png)
 �ɹ���װmysql

 ��3�����԰�װ�Ƿ�ɹ�&&���ص�¼mysql����
 ```
 sudo netstat -tap|grep mysql
 mysql -uroot -p
 ```
 ![mysql3](./pictures/mysql3.png)

 ��4�������ݿ���м򵥲��� �����Ͳ鿴����
 ```
 create database bxh;
 shwget http://php.net/distributions/php-7.2.2.tar.gz ow databases;
 ```
 ![mysql4](./pictures/mysql4.png)

---
## 4.**Php**
(1)����php�ļ�
```
wget https://php.net/distributions/php-7.2.2.tar.gz
```
![php1](./pictures/php1.png)
��2����ѹ
```
tar -zxvf php-7.2.2.tar.gz
```
��3�������ѹĿ¼
```
cd php-7.2.2
```
��4��Ԥ����
```
sudo ./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc --enable-fpm
```
---
**���ֵ�����**��

![php2](./pictures/php2.png)
**����ԭ��**��

û�а�װlibxml2

**������**��
```
 sudo apt-get install libxml2
 sudo apt-get install libxml2-dev
```

---
����ִ��Ԥ����ָ���
![php4](./pictures/php4.png)

��5������php
```
sudo make
```
������������**�ܳ�һ��ʱ��**�ı��룬���ڱ���ɹ��ˣ���Լ����ʮ�������ң�����CPU ��ռ���˲��٣����ȵ�����Ҳʮ�ִ�

![php5](./pictures/php5.png)

��6����װphp
```
sudo install php
```
![php6](./pictures/php6.png)
��7���޸������ļ�
```
cd /usr/local/php/etc 
sudo cp php-fpm.conf.default php-fpm.conf 
cd /usr/local/php/etc/php-fpm.d 
sudo cp www.conf.default www.conf 
```

���www�û�����
```
sudo groupadd www 
sudo useradd -g www www 
```
�޸�www.conf�е���������û�
```
user=www
group=www
```
![php7](./pictures/php7.png)

��8���޸�nginx.conf��֧��php-fpm

��9������php�����ļ�
��/usr/local/nginx/html �´���index.php�ļ�
 ```
 <?php
  echo phpinfo();
 ?>
 ```
 ��10������php-fpm���� nginx����������
 ```
 /usr/local/php/sbin/php-fpm start
 ```
 ��11�����������
 http://localhost/index.php
 ![php10](./pictures/php10.png)
 


## 5.**Wordpress**

��1��׼����װwordpress���ݿ�

   *��root��ݽ���mysql*
```
sudo mysql -u root
```
 *����һ��wordpress���ݿ�*
 ```
 create database wordpress;
```
*����һ���û�bxh������wordpress���ݿ��ȫ��Ȩ��*
```
create user 'bxh' identified by '1113';
grant all privileges on wordpress.* to 'bxh';
```
*�˳�*
```
quit
```

��2������wordpress��װ��
```
wget https://cn.wordpress.org/wordpress-4.7.4-zh_CN.zip
```
![w1](./pictures/w1.png)

---
**���ֵ�����**������429��Too many requests.

**�����ԭ��**��
1. ���������й���½�������� wordpress.org �������ҹ�����

2. �������������CDN�����½�ķ���������Nginx��Ը������Զ�ͣ�ڡ�

3. �����еİ����߲���֪�������½��CDN��������������Լ��ܷ���������Ϊû���⡣

**����Ľ��**��

1. ����WordPress���ص�ַ

   Ӣ�İ��ַ��https://wordpress.org/latest.zip

   ���İ��ַ��https://cn.wordpress.org/latest-zh_CN.zip

2. ��������������磺Ѹ�� �����½���������

3. ����ճ����������ص�ַ�������������ˡ�

   ���ͨ��X-FTP�ϴ����°�WordPress�����������ֶ����¼��ɡ�
---
��3����wordpress��װ����ѹ�����õ�nginx�������ĸ�Ŀ¼��������/var/www/html/wordpress

��4���������������*https://localhost/wordpress*,���Զ���ʼwordpress�İ�װ

![w2](./pictures/w2.png)

��4�����let's go��Ȼ����֮ǰ��mysql���洴����wordpress���ݿ���д��Ӧ��username��password��Ȼ����submit��ť������һ��

��5����֮ǰnginx��Ŀ¼��/var/www/html/wordpress��Ŀ¼�����½�һ��wp-config.php�ļ���������������ֵĴ��븴�Ƶ�wp-config.php�ļ����棬Ȼ������Run the installation����ť������һ����װ��
![w3](./pictures/w3.png)

��6����д��վ���ƣ���̨����Ա�û�������̨���룬��ϵ������Ϣ�����ҵ��ͬ��������Ȼ������Install Wordpress����ť����ʼ��ʽ�İ�װwordpress����

---
**���ֵ����⼰���**��*��Discourage search engines from indexing this site�����ѡ��ܹ�ѡ����Ȼ�Ļ���������Ͳ�����¼wordpressվ���ˣ�*
---
---
��7����װ�ɹ���Ȼ���������ݿ������õ��û��������뼴�ɽ��뵽wordpress�ĺ�̨

![w4](./pictures/w4.png)

��8���ɹ���װwordpress

ps������wordpress�ļ򵥽���

**WordPress��ʹ��PHP���Կ����Ĳ���ƽ̨���û�������֧��PHP��MySQL���ݿ�ķ������ϼ��������Լ�����վ��Ҳ���԰� WordPress����һ�����ݹ���ϵͳ��CMS����ʹ�á�
WordPress��һ����˲���ϵͳ�������ݻ���һ�����ݹ���ϵͳ���������ʹ��PHP���Ժ�MySQL���ݿ⿪����,�û�������֧�� PHP �� MySQL���ݿ�ķ�������ʹ���Լ��Ĳ��͡�**  --�ٶȰٿ�

---
�ܽ᣺������������װ�����ã����ǳɹ��Ĵ��lnmp����+wordpress���ڰ�װ�����õĹ����˸�����Ϥ��linux�µ�shellָ�����Լ�linux���ļ���֯�ṹ���˽��˸����ļ��е����ú͹��ܣ�Ϊ��������linux��linux���ſε�ѧϰ���������õĻ�����ͨ���Լ��������ð�װ���������������ǵĶ������������ڼ�¼��װ���뿪���Ĺ����ж����������ĵ�����д�����������֯���Լ������ù��̲������ĵ���ʽ��¼��ʮ����Ҫ�ģ�Ϊ���ĸ��õ�ѧϰlinux���������õĻ�����




