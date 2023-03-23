Configuración almacén ops.soft ukar mantam, `./ssl.sh` ukar mantam, ukatx mä carpeta `conf` ukaw lurasini **altu directorio** ukan .

## nayrïr arunaka

SMTP ukax chiqapuniw cloud aljirinakatxa servicios ukanakax alasispa, sañäni:

* [Amazon SES SMTP ukax mä juk’a pachanakanwa](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
* [Ali cloud correo electrónico ukax mä juk’a pachanakanwa](https://www.alibabacloud.com/help/directmail/latest/three-mail-sending-methods)

Ukhamarakiw juma pachpax correo servidor ukar luraraksna - jan tukuskir apayani, taqpach qullqix juk’akiw.

Aka aynachanxa, kunjamsa jiwasana pachpa servidor de correo lurañasa ukxa mä juk’a pachana uñacht’ayapxtha.

## Servidor ukax ajllitawa

Servidor SMTP auto-hosted ukax mä IP público ukaruw munaraki, ukax puertos 25, 456 ukat 587 jist’aratawa.

Sapa kuti apnaqat clouds públicos ukanakax uka puertos ukanakaruw jark’antapxi, ukatx inas mä orden de trabajo ukar apsusaw jist’arañax wakischispa, ukampis taqi kunat sipanx wali jan walt’awiwa.

Nayax mä host ukan alañ iwxt’sma, ukax uka puertos jist’aratawa ukatx dominio inverso sutinak utt’ayañ yanapt’i.

Aka chiqanx, [Contabo](https://contabo.com) ukar iwxt’apxsma.

Contabo ukax mä alojamiento ukaw Múnich, Alemania markan utt’ayata, 2003 maran utt’asiwayi, wali ch’axwañ chaninakampi.

Euro qullqix alañ qullqit ajllitäni ukhax chanipax juk’amp jila chaniniw (mä servidor 8GB memoria ukat 4 CPUs ukax niya 529 yuanes ukharuw sapa marax aljasi, ukatx qallta instalación qullqix mä maratakiw inakiw).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/UoAQkwY.webp)

Kunawsatix mä pedido lurasktan ukhax remark `prefer AMD` , ukatx servidor ukax AMD CPU ukampiw juk’amp suma lurawinïni.

Aka tuqinx Contabo ukan VPS ukarux mä uñacht’äwiw apsuñ munta, kunjams juma pachpan servidor de correo ukar lurañax uk uñacht’ayañataki.

## Ubuntu sistema ukax wakicht’atawa

Aka chiqanx sistema operativo ukax Ubuntu 22.04 ukawa

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/smpIu1F.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/m7Mwjwr.webp)

Ukax ssh ukan servidor uñacht’ayi `Welcome to TinyCore 13!` (kunjamtix aka uñacht’awix uñacht’ayaski ukhamarjama), ukax sañ muniw sistema ukax janiw jichhakamax utjkiti. Ukhamaraki, ssh ukat mä qawqha minutos suyt’añamawa, ukhamat wasitat mantañataki.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/-qKACz9.webp)

Kunawsatix `Welcome to Ubuntu 22.04.1 LTS` uñstki ukhax qalltawix tukuyatawa, ukatx aka lurawinakampiw sarantaskakini.

### [Opcional] Nayrar sartañ pacha qalltaña

Aka lurawixa opcional ukhamawa.

Jan ch’amäñapatakix, ubuntu software ukan instalación ukat sistema configuración ukar [github.com/wactax/ops.os/tree/main/ubuntu](https://github.com/wactax/ops.os/tree/main/ubuntu) ukar uñt’ayawayta.

Mä ch’iqtañampiwa instalañatakixa aka kamachi phuqhaña.

```
bash <(curl -s https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

Chino apnaqirinakaxa, uka lanti aka kamachi apnaqapxañani, ukatxa aru, zona horaria, juk’ampinaka ukaxa automáticamente uñt’ayatarakiniwa.

```
CN=1 bash <(curl -s https://ghproxy.com/https://raw.githubusercontent.com/wactax/ops.os/main/ubuntu/boot.sh)
```

### Contabo ukax IPV6 ukaruw yanapt’i

IPV6 ukar ch’amanchaña ukhamat SMTP ukax IPV6 ukan direccionanakapamp correo electrónico ukar apayaniñapataki.

`/etc/sysctl.conf` ukar mayjt’ayaña

Aka chimpunak mayjt’ayaña jan ukax yapxataña

```
net.ipv6.conf.all.disable_ipv6 = 0
net.ipv6.conf.default.disable_ipv6 = 0
net.ipv6.conf.lo.disable_ipv6 = 0
```

[Contabo yatichawimpi arktañani: IPv6 ukampi chikt’atäña servidor ukar yapxataña](https://contabo.com/blog/adding-ipv6-connectivity-to-your-server/)

`/etc/netplan/01-netcfg.yaml` chiqañchaña, mä qawqha chimpunak yapxataña kunjamtix aka uñacht’ayat uñacht’ayaski ukhama (Contabo VPS configuración predeterminada archivo ukax nayratpach uka chimpunakax utjiwa, ukakipkarakiw jan amuyt’ayañaki).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/5MEi41I.webp)

Ukatx `netplan apply` .

Uka wakicht’awix wali askiwa, `curl 6.ipw.cn` ukampiw anqäx red ukan ipv6 ukar uñakipañatakix apnaqasispa.

## Clonar ukax configuración ukan imañ uta ops

```
git clone https://github.com/wactax/ops.soft.git
```

## Mä SSL certificado inaki luraña dominio sutimpi

Correo apañatakix mä certificado SSL ukax encriptación ukat firmañatakix wakisiwa.

Jiwasax [acme.sh uka](https://github.com/acmesh-official/acme.sh) apnaqapxta certificados ukanaka lurañataki.

acme.sh ukax mä herramienta de código abierto automático certificado firmañatakiwa,

Configuración almacén ops.soft ukar mantam, `./ssl.sh` ukar mantam, ukatx mä carpeta `conf` ukaw lurasini **altu directorio** ukan .

DNS ukax [acme.sh dnsapi](https://github.com/acmesh-official/acme.sh/wiki/dnsapi) ukan jikxatañamawa, `conf/conf.sh` ukar chiqañchañamawa.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Qjq1C1i.webp)

Ukatxa `./ssl.sh 123.com` `123.com` ukatxa `*.123.com` certificados ukanaka lurañataki dominio sutipataki.

Nayrïr t’ijtawix [acme.sh ukarux](https://github.com/acmesh-official/acme.sh) automáticamente uñstayañapawa ukatx mä programado luraw yapxatañapawa automáticamente machaqar tukuyañataki. Uñxatt’añatakix `crontab -l` , ukax akham chimpuniwa.

```
52 0 * * * "/mnt/www/.acme.sh"/acme.sh --cron --home "/mnt/www/.acme.sh" > /dev/null
```

Uñstayata certificado ukatakix thakhix mä kunayman `/mnt/www/.acme.sh/123.com_ecc。`

Certificado machaqar tukuyañax `conf/reload/123.com.sh` script ukaruw jawsani, aka script ukar chiqañchañamawa, kamachinak yapxatañamawa kunjamatix `nginx -s reload` ukax certificado caché ukar machaqar tukuyañataki.

## SMTP servidor ukax chasquid ukampiw lurasi

[chasquid](https://github.com/albertito/chasquid) ukax mä servidor SMTP abierto de código fuente ukawa, ukax Go arun qillqt’atawa.

Nayra programas de servidor de correo ukanakar lantintañataki, Postfix ukat Sendmail, chasquid ukax juk’amp sapuru ukat juk’amp jasakiw apnaqañataki, ukatx secundario desarrollo ukatakix juk’amp jasakiwa.

Run `./chasquid/init.sh 123.com` mä clic ukampiw automáticamente uñstayatäni (123.com ukax khithañ dominio sutimpiw turkañapa).

## Correo electrónico Firma DKIM ukar uñt’ayaña

DKIM ukax correo electrónico ukan firmanakapar apayañatakiw apnaqasi, ukhamat qillqatanakax jan spam ukham uñjatäñapataki.

Kamachixa suma phuqhata tukuyatatxa, DKIM qillqawi utt’ayañatakixa mayitawa (kunjamatixa akhamawa uñacht’ayata).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/LJWGsmI.webp)

Mä TXT registro DNS ukar yapxatañakiw wakisi (kunjamtix akham uñacht’ayaski).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/0szKWqV.webp)

## Servicio estado & registros uñakipaña

 `systemctl status chasquid` Uñakipt’aña servicio estado.

Estado de operación normal ukaxa kunjamatixa uñacht’ayata aka uñacht’awina

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/CAwyY4E.webp)

 `grep chasquid /var/log/syslog` jan ukax `journalctl -xeu chasquid` pantjasiw qillqat uñakipt’aspawa.

## Reverso dominio suti uñakipaña

Uka reverso dominio sutixa IP uñt’ayawixa askichañataki ukhamaraki uñt’ayata dominio sutimpi.

Mä reverso dominio suti utt’ayañax correo electrónico ukanakax jan spam ukham uñt’ayasiñapatakiw jark’aspa.

Kunawsatix correo ukax katuqatäki ukhax katuqir servidor ukax reverso dominio suti uñakipañ lurani IP ukan IP ukanx khithañ servidor ukan chiqaparu reverso dominio sutimp uñt’ayañataki.

Uka khithañ servidor ukax janiw mä reverso dominio sutinïkiti jan ukax reverso dominio sutix jan IP ukarjam khithañ servidor ukar uñtasitäkchi ukhaxa, katuqir servidor ukax correo electrónico ukarux spam ukham uñt’ayaspawa jan ukax janiw sasaw uñt’ayaspa.

[https://my.contabo.com/rdns](https://my.contabo.com/rdns) ukar mantam ukat kunjamtix akham uñacht’ayaski ukhamarjam wakicht’añamawa

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/IIPdBk_.webp)

Ukatxa, reverso dominio suti utt’ayaña tukuyatatxa, amtañawa configuración forward resolution uka dominio suti ipv4 ukatxa ipv6 uka servidor ukaru.

## chasquid.conf ukan uñt’ayawip uñt’ayaña

`conf/chasquid/chasquid.conf` mayjt’ayatawa, ukax reverso dominio sutimp uñt’atawa.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/6Fw4SQi.webp)

Ukatxa `systemctl restart chasquid` lurañawa, ukhamata servicio ukaxa mayampi qalltañataki.

## Conf ukax git imañ utar uñtatawa

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/Fier9uv.webp)

Amuyt’añataki, nayax conf carpeta ukax nayan pachpa github proceso ukaruw mä copia de seguridad lurta

Nayraqatax mä almacén privado luraña

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ZSCT1t1.webp)

Uka conf directorio ukar mantam ukat almacén ukar uñt’ayañamawa

```
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin git@github.com:wac-tax-key/conf.git
git push -u origin main
```

## Khitirimpi yapxataña

jalaña

```
chasquid-util user-add i@wac.tax
```

Khijiri yapxataspawa

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/khHjLof.webp)

### Uka contraseña ukaxa chiqapa utt’ayatawa

```
chasquid-util authenticate i@wac.tax --password=xxxxxxx
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/e92JHXq.webp)

Usuario yapxatañ tukuyatatxa, `chasquid/domains/wac.tax/users` machaqar tukuyatäni, amtañaniw almacén ukar uñt’ayaña.

## DNS ukax SPF qillqatan yapxatatawa

SPF ( Marco de Políticas de Enviador ) ukax mä tecnología de verificación de correo electrónico ukawa, ukax correo electrónico ukar jan sallqjañatakiw apnaqasi.

Ukax mä correo apayirin identidad ukar chiqanchañatakiw uñakipi, khitin IP ukax registros DNS ukampiw uñt’ayasi, ukax dominio sutimp uñt’atawa, ukax sallqjirinakax k’ari correo electróniconak apayapxañapatakiw jark’i.

SPF qillqatanaka yapxatañax correo electrónico ukanakax spam ukham uñt’ayasiñapatakiw jark’aqaspa.

Uka dominio suti servidor ukax janiw SPF tipo ukar yanapt’kiti, ukax TXT tipo registro ukar yapxatañakiw wakisi.

Amuyt’añataki, SPF de `wac.tax` ukax akhamawa

`v=spf1 a mx include:_spf.wac.tax include:_spf.google.com ~all`

SPF ukax `_spf.wac.tax` ukatakiw

`v=spf1 a:smtp.wac.tax ~all`

Qhanacht’añatakix akanx `include:_spf.google.com` ukaw utjitu, akax kunatix nayax `i@wac.tax` ukaruw qhipharux Google ukan correo ukan khitañ utar uñt’ayaskä.

## DNS ukan utt’ayata DMARC

DMARC ukax (Autenticación de Mensajes basadas en dominio, Reporting & Conformance) uka jisk’a arumpiw uñt’ayasi.

Ukax SPF rebotes ukanakar katjañatakiw apnaqasi (inas configuración pantjasiwinakat utjchispa, jan ukax yaqhax jumar uñtasitaw spam apayanisma).

TXT qillqata `_dmarc` , .

Uka tuqitxa akhamawa

```
v=DMARC1; p=quarantine; fo=1; ruf=mailto:ruf@wac.tax; rua=mailto:rua@wac.tax
```

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/k44P7O3.webp)

Sapa parámetro ukan amuyupax akhamawa

### p (Política) 1.1.

Kunjams correo electróniconak apnaqañ uñacht’ayi, ukax SPF (Marco de Políticas de Enviador) jan ukax DKIM (DomainKeys Identified Mail) chiqanchañ jan walt’ayatawa. Parámetro p ukax kimsa chimpunakat mayniruw uñt’ayasispa:

* janiw kunas utjkiti: Janiw kuna lurawis luratäkiti, chiqanchañ resultado ukakiw khitirus apayatax mecanismo de informe de correo electrónico tuqi.
* Cuarentena: Uka correo ukaxa janiwa chiqapa pasañapatakixa carpeta de spam ukarux uchañakiti, ukampisa janiwa chiqak uka correo ukarux jan iyawskaniti.
* reject: Chiqpachanx correo electróniconak jan chiqapar uñjañ jan iyawsaña.

### fo (Janiw kunas utjkiti) .

Yatiyawi mecanismo tuqi yatiyawi kutt’ayaña qhananchaña. Ukax mä chimpuruw uñt’ayasispa:

* 0: Taqi yatiyawinakat chiqanchañ yatiyäwinak yatiyaña
* 1: Yatiyawinak yatiyañakiw jan chiqapar uñjañjamakiti
* d: Dominio suti chiqanchañ jan walt’awinak yatiyañakiw wakisi
* s: SPF chiqapar uñjañ jan walt’awinak yatiyañakiw wakisi
* l: DKIM ukan chiqanchawipan jan walt’awinakapat yatiyañakiw wakisi

### rua & ruf ukat juk’ampinaka

* rua (URI yatiyaña Yatiyawinak Agregado): Correo electrónico ukax yatiyawinak apthapit katuqañataki
* ruf (URI yatiyaña Forense yatiyawinakataki): correo electrónico ukar uñt’ayaña suma yatiyawinak katuqañataki

## MX qillqatanakax Google Mail ukar correo electrónico ukar apañatakix yapxatatawa

Kunatix janiw mä caja de correo corporativa inaki jikxatkti, ukax direcciones universales ukar yanapt’i (Catch-All, kuna correo electrónicos ukanak aka dominio sutir apayatax katuqasispawa, jan prefijos ukar jark’ata), chasquid ukampiw taqi correo electróniconak Gmail ukar apayañatak apnaqawayta.

**Jumatix payllat negocio correo ukanx utjktam ukhax janiw MX ukar mayjt’ayañamäkiti ukat aka lurawix jaytañawa.**

`conf/chasquid/domains/wac.tax/aliases` chiqañchaña, correo ukar apayañ uñt’ayaña

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/OBDl2gw.webp)

`*` taqi correo electrónico uñacht’ayi, `i` ukax khithañ apnaqirin correo electrónico ukan nayrïr chimpupawa, ukax akham luratawa. Correo apayañatakix sapa mayni apnaqirix mä chimpu yapxatañapawa.

Ukatx MX qillqat yapxataña (aka chiqanx dominio inverso sutimp chiqak uñacht’ayaraktwa, kunjamatix nayrïr chimpunx uñacht’ayaski ukhamarjama).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/7__KrU8.webp)

Configuración ukax tukuyatatxa, yaqha correo electrónico ukanakamp `i@wac.tax` ukat `any123@wac.tax` ukaruw correo electrónico apayanisma, Gmail ukan correo electróniconak katuqañax wakisispati janicha uk uñjañataki.

Jan ukhamäkchi ukhaxa, chasquid registro ( `grep chasquid /var/log/syslog` ) uñakipt’añamawa.

## Mä correo electrónico i@wac.tax ukaruw Google Mail ukamp apayanisma

Google Mail ukax correo katuqañ tukuyatatx ​​naturalmente `i@wac.tax` ukampiw jaysañ suyt’awayta, janiw i.wac.tax@gmail.com ukampiw jaysañ munta.

[https://mail.google.com/mail/u/1/#settings/accounts](https://mail.google.com/mail/u/1/#settings/accounts) ukar mantam ukat "Yaqha correo electrónico ukar yapxatam" ukx ch'iqt'am.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/PAvyE3C.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/_OgLsPT.webp)

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/XIUf6Dc.webp)

Ukatxa, uka correo electrónico ukax katuqatäki uka código de verificación ukax uñt’ayatarakiwa.

Tukuyañatakix, khitirus khithañ utar uñt’ayañax wakisispawa (uka pachpa uñt’ayawimp jaysañ amtawimp chika).

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/a95dO60.webp)

Ukhamatwa, SMTP correo servidor ukan utt’ayasiñ tukuyapxta ukatx pachpa pachanx Google Mail ukampiw correo electrónico ukar apañataki ukat katuqañataki.

## Mä yant’äw correo electrónico apayanipxam, ukax configuración ukax walikiti janicha uk uñakipañataki

Uka `ops/chasquid` ukar mantañamawa

Run `direnv allow` instalar dependencias (direnv ukax nayrir mä llave qalltañ lurawinx utt’ayatawa ukatx mä gancho ukax shell ukar yapxatatawa)

ukatsti t’ijtxa

```
user=i@wac.tax pass=xxxx to=iuser.link@gmail.com ./sendmail.coffee
```

Uka parámetros ukanakan amuyupax akhamawa

* apnaqiri: SMTP apnaqirin sutipa
* pasa: SMTP ukax mä juk’a pachanakanwa
* ukat: katuqiri

Mä yant’äw correo electrónico apayanisma.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/ae1iWyM.webp)

Gmail apnaqañax wali askiwa yant’äw correo electróniconak katuqañataki, ukhamat configuración ukanakax askinjam phuqhaskiti janicha uk uñakipañataki.

### TLS ukax mä encriptación estándar ukawa

Kunjamatixa uñacht’ayata aka uñacht’awina, aka jisk’a bloqueo ukaw utji, ukax sañ muniw SSL certificado ukax suma ch’amanchatawa.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/SrdbAwh.webp)

Ukatxa "Correo electrónico Original uñacht'ayaña" ukxaru ch'iqt'aña.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/qQQsdxg.webp)

### DKIM ukax mä juk’a pachanakanwa

Kunjamatix aka uñacht’awix uñacht’ayaski, Gmail original correo ukanx DKIM uñacht’ayi, ukax sañ muniw DKIM ukan configuración ukax wali askiwa.

![](https://pub-b8db533c86124200a9d799bf3ba88099.r2.dev/2023/03/an6aXK6.webp)

Uñakipt’añatakix Received ukax p’iqinchaw nayrïr correo electrónico ukan p’iqinchatawa, ukatx uñjañamawa khitirus apayirix IPV6 ukawa, ukax sañ muniw IPV6 ukax suma wakicht’atarakiwa.
