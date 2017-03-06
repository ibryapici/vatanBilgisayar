# Vatan Bilgisayar Ürün Çekme Scripti
phpQuery ile Vatan Bilgisayar notebook kategorisindeki ürünlerin başlık, link, resim ve fiyat değerlerini kolaylıkla alabilirsiniz.

```php
require('phpQuery/phpQuery.php');


$siteLinki = "http://www.vatanbilgisayar.com/notebook/";

phpQuery::newDocumentFileHTML($siteLinki);
$urunler = array();
foreach(pq('li.ems-prd') as $li){
	$urunler[] = array(
					"link"=> pq($li)->find('div.ems-prd-name a')->attr('href'),
					"baslik"=> pq($li)->find('div.ems-prd-name a')->text(),
					"img" => pq($li)->find('div.ems-prd-image a img')->attr('data-original'),
					"price" => pq($li)->find('div.urunListe_satisFiyat')->text()
				);
	
} 
foreach($urunler as $urun)
{
	?>
	<h5><?php echo $urun['img']; ?></h5>
	<img style = "width:150px; height:auto" src = "<?php echo $urun['img']; ?>"/>
	<h4>
		<?php echo $urun['baslik']; ?>
	</h4>
	<a href = "www.vatanbilgisayar.com<?php echo $urun['link']; ?>">www.vatanbilgisayar.com<?php echo $urun['link']; ?></a>
	<h5>
		<?php echo $urun['price']; ?>
	</h4>
	<hr>
	<?php
}
```

Deyatlı bilgi için iletişime geçebilirsiniz.
