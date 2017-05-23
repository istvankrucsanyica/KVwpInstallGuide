# Telepítéskor elvégezendő feladatok

* Igyekezzünk letölteni a legfrissebb WordPress verziót a hivatalos [weboldalról](https://wordpress.org/download/).
* Minden esetben változtassuk meg az adatbázis tábla előtagjának nevét az alapértelmezett `wp_` előtag helyett.
* A telepítés végeztével töröljük a wp-config-sample file-t.
* 
	```
	wp-config-sample.php
	```
	
* Rejtsük el a fejlesztendő oldalunkat a kereső robotok elől. (Beállítások > Olvasás)
* Állítsuk be a helyes időzónát. (Beállítások > Általános)
* Használjuk a [KVwpBaseFunctions](https://github.com/istvankrucsanyica/KVwpBaseFunctions)-t a téma fejlesztése során.
* Használjuk a [KVwpBaseHtaccess](https://github.com/istvankrucsanyica/KVwpBaseHtaccess)-t.


&nbsp;

&nbsp;

# `wp-config.php` beállítások [opcionális]
>Bővebb információk az alábbi [linken](https://codex.wordpress.org/Editing_wp-config.php)

&nbsp;

**Keys and Salts**

Minden esetben generáljunk új Salt kulcsokat. Az alábbi [linkre](https://api.wordpress.org/secret-key/1.1/salt/) kattintva automatikusan megkapjuk az új kulcsokat.

&nbsp;

**Limitáljuk a mentésre kerülő Változatok számát**

```php
define( 'WP_POST_REVISIONS', '2' );
```
Ebben az esetben minden bejegyzésből maximálisan a két legutolsó változat kerül mentésre.

&nbsp;

**Lomtár űrítése**

```php
define( 'EMPTY_TRASH_DAYS', '31' );
```
Az alapértelmezett beállítás szerint 30 nap után törlődnek a lomtárba helyezett bejegyzések, az `EMPTY_TRASH_DAYS` után megadott számértékkel megváltoztathatjuk ezt.

A lomtár funkciót elérhetővé tudjuk tenni a **Médiatár** számára is:

```php
define( 'MEDIA_TRASH', true );
```

&nbsp;

**Az automatikus mentés idejének megváltoztatása**

Az alapértelmezett 60 másodperc helyett megadhatunk tetszőleges időtartamot is:

```php
define( 'AUTOSAVE_INTERVAL', '120' );
```

&nbsp;

**A WordPress admin sablon és plugin szerkesztőjének kikapcsolása**

Ezt a funckiót letiltva az adminisztrátorok nem tudják a sablon file-okat és bővítményeket szerkeszteni a vezérlőpulton keresztül, így egy biztonsági rést is elzárunk.

```php
define( 'DISALLOW_FILE_EDIT', true );
```

&nbsp;

**Sablonok, bővítmények telepítésének és frissítésének tiltása**

Letiltja a felhasználók elől a bővítmények hozzáadásának és frissítésének lehetőségét.

```php
define( 'DISALLOW_FILE_MODS', true );
```

&nbsp;

**Az automatikus frissítés funkció kikapcsolása**

A rendszerünk nem fog automatikusan frissülni, ugyanakkor továbbra is megkapjuk az frissítési értesítéseket.

```php
define( 'WP_AUTO_UPDATE_CORE', false );
```

&nbsp;

&nbsp;

# Élesítéskor elvégzendő feladatok

* Tegyük láthatóvá az oldalt a keresők számára. (Beállítások > Olvasás)
* Töltsük fel a `robots.txt`-t

	```
	User-Agent: *
	Disallow: /wp-admin/
	Disallow: /admin_login
	Disallow: /cgi-bin
	Disallow: /wp-includes/
	Disallow: /wp-content/plugins/
	Disallow: /wp-content/cache/
	Disallow: /wp-content/themes/
	Sitemap: http://domain.com/sitemap.xml
	```
	
* Ellenőrizzük, hogy az oldal megfelelően megosztható-e, minden helyesen jelenik-e meg a megosztáskor. [opengraphcheck.com](http://opengraphcheck.com)
* Ellenőrizzük le, hogy a Süti értesítő megfelelően megjelenik az oldalon.
* Favikonok feltöltése