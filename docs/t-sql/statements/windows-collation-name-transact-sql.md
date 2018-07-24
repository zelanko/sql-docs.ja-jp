---
title: Windows 照合順序名 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Windows collations [SQL Server]
- names [SQL Server], collations
- collations [SQL Server], Windows collations
- Collation Designator
ms.assetid: acceef84-2c68-46e2-a021-be019b7ab14e
caps.latest.revision: 43
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1be59e84a5b40444e6218c2b390b832516193ecf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982281"
---
# <a name="windows-collation-name-transact-sql"></a>Windows 照合順序名 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で COLLATE 句に Windows 照合順序名を指定します。 Windows 照合順序名は、照合順序指定子と比較形式で構成されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
<Windows_collation_name> :: =   
CollationDesignator_<ComparisonStyle>  
  
<ComparisonStyle> :: =   
{ CaseSensitivity_AccentSensitivity  [ _KanatypeSensitive ] [ _WidthSensitive ]    
}  
| { _BIN | _BIN2 }  
```  
  
## <a name="arguments"></a>引数  
 *CollationDesignator*  
 Windows 照合順序で使用される基本照合順序規則を指定します。 基本照合順序規則には、次の要素が含まれます。  
  
-   辞書順での並べ替えを指定した場合に適用される並べ替え規則。 並べ替え規則は、アルファベットまたは言語に基づきます。  
  
-   Unicode 以外の文字データの格納に使用するコード ページ。  
  
 次にいくつかの例を挙げます。  
  
-   Latin1_General または French: 両方ともコード ページ 1252 が使用されます。  
  
-   Turkish: コード ページ 1254 が使用されます。  
  
 *CaseSensitivity*  
 **CI** を指定すると大文字小文字は区別されず、**CS** を指定すると大文字小文字が区別されます。  
  
 *AccentSensitivity*  
 **AI** を指定するとアクセントは区別されず、**AS** を指定するとアクセントが区別されます。  
  
 *KanatypeSensitive*  
 **Omitted** を指定するとかなは区別されず、**KS** を指定するとかなが区別されます。  
  
 *WidthSensitivity*  
 **Omitted** を指定すると文字幅は区別されず、**WS** を指定すると文字幅が区別されます。  
  
 **BIN**  
 旧バージョンとの互換性のあるバイナリ並べ替え順を使用します。  
  
 **BIN2**  
 コード ポイントの比較セマンティクスを使用するバイナリ並べ替え順を指定します。  
  
## <a name="remarks"></a>Remarks  
 照合順序のバージョンによっては、一部のコード ポイントは未定義の場合があります。 たとえば、次の比較を行います。  
  
```  
SELECT LOWER(nchar(504) COLLATE Latin1_General_CI_AS);   
SELECT LOWER (nchar(504) COLLATE Latin1_General_100_CI_AS);  
GO  
```  
  
 照合順序が Latin1_General_CI_AS の場合、最初の行によって大文字が返されます。このコード ポイントはこの照合順序では未定義であるためです。  
  
 一部の言語では、古い照合順序を回避すると重大な結果となる可能性があります。 たとえば、Telegu がこれに該当します。  
  
 Windows 照合順序と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序で、同じクエリに対して異なるクエリ プランが生成される場合があります。  
  
## <a name="examples"></a>使用例  
 次に Windows 照合順序名の例をいくつか示します。  
  
-   **Latin1_General_100_**  
  
 照合順序に、Latin1 一般辞書の並べ替え規則とコード ページ 1252 が使用されます。 大文字と小文字は区別されず、アクセントは区別されます。 照合順序に、Latin1 一般辞書の並べ替え規則が使用され、コード ページ 1252 と対応付けられます。 Windows 照合順序の場合は、照合順序のバージョン番号 (_90 または _100) が表示されます。 大文字と小文字は区別されず (CI)、アクセントは区別されます (AS)。  
  
-   **Estonian_CS_AS**  
  
     照合順序に、エストニア語辞書の並べ替え規則とコード ページ 1257 が使用されます。 大文字と小文字およびアクセントが区別されます。  
  
-   **Latin1_General_BIN**  
  
     照合順序に、コード ページ 1252 とバイナリ並べ替え規則が使用されます。 Latin1 一般辞書の並べ替え規則は無視されます。  
  
## <a name="windows-collations"></a>Windows 照合順序  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでサポートされている Windows 照合順序の一覧を表示するには、次のクエリを実行します。  
  
```  
SELECT * FROM sys.fn_helpcollations() WHERE name NOT LIKE 'SQL%';  
```  
  
 次の表に、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされるすべての Windows 照合順序を示します。  
  
|Windows ロケール|照合順序バージョン 100|照合順序バージョン 90|  
|--------------------|---------------------------|--------------------------|  
|アルザス語 (フランス)|Latin1_General_100_|使用不可|  
|アムハラ語 (エチオピア)|Latin1_General_100_|使用不可|  
|アルメニア語 (アルメニア)|Cyrillic_General_100_|使用不可|  
|アッサム語 (インド)|Assamese_100_ <sup>1</sup>|使用不可|  
|バシキール語 (ロシア)|Bashkir_100_|使用不可|  
|バスク語 (バスク)|Latin1_General_100_|使用不可|  
|ベンガル語 (バングラデシュ)|Bengali_100_<sup>1</sup>|使用不可|  
|ベンガル語 (インド)|Bengali_100_<sup>1</sup>|使用不可|  
|ボスニア語 (ボスニア・ヘルツェゴビナ、キリル文字)|Bosnian_Cyrillic_100_|使用不可|  
|ボスニア語 (ボスニア・ヘルツェゴビナ、ラテン文字)|Bosnian_Latin_100_|使用不可|  
|ブルトン語 (フランス)|Breton_100_|使用不可|  
|中国語 (中華人民共和国マカオ特別行政区)|Chinese_Traditional_Pinyin_100_|使用不可|  
|中国語 (中華人民共和国マカオ特別行政区)|Chinese_Traditional_Stroke_Order_100_|使用不可|  
|中国語 (シンガポール)|Chinese_Simplified_Stroke_Order_100_|使用不可|  
|コルシカ語 (フランス)|Corsican_100_|使用不可|  
|クロアチア語 (ボスニア・ヘルツェゴビナ、ラテン文字)|Croatian_100_|使用不可|  
|ダリー語 (アフガニスタン)|Dari_100_|使用不可|  
|英語 (インド)|Latin1_General_100_|使用不可|  
|英語 (マレーシア)|Latin1_General_100_|使用不可|  
|英語 (シンガポール)|Latin1_General_100_|使用不可|  
|フィリピノ語 (フィリピン)|Latin1_General_100_|使用不可|  
|フリジア語 (オランダ)|Frisian_100_|使用不可|  
|グルジア語 (グルジア)|Cyrillic_General_100_|使用不可|  
|グリーンランド語 (グリーンランド)|Danish_Greenlandic_100_|使用不可|  
|グジャラート語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|ハウサ語 (ナイジェリア、ラテン文字)|Latin1_General_100_|使用不可|  
|ヒンディー語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|イボ語 (ナイジェリア)|Latin1_General_100_|使用不可|  
|イヌクティトット語 (カナダ、ラテン文字)|Latin1_General_100_|使用不可|  
|イヌクティトット語 (音節文字) カナダ|Latin1_General_100_|使用不可|  
|アイルランド語 (アイルランド)|Latin1_General_100_|使用不可|  
|日本語 (日本 XJIS)|Japanese_XJIS_100_|Japanese_90_、Japanese_|  
|日本語 (日本)|Japanese_Bushu_Kakusu_100_|使用不可|  
|カンナダ語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|クメール語 (カンボジア)|Khmer_100_<sup>1</sup>|使用不可|  
|キチェ語 (グアテマラ)|Modern_Spanish_100_|使用不可|  
|キニヤルワンダ語 (ルワンダ)|Latin1_General_100_|使用不可|  
|コーンクニー語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|ラオス語 (ラオス人民民主共和国)|Lao_100_<sup>1</sup>|使用不可|  
|下ソルブ語 (ドイツ)|Latin1_General_100_|使用不可|  
|ルクセンブルク語 (ルクセンブルク)|Latin1_General_100_|使用不可|  
|マラヤーラム語 (インド)|Indic_General_100_<sup>1</sup>|使用不可|  
|マルタ語 (マルタ)|Maltese_100_|使用不可|  
|マオリ語 (ニュージーランド)|Maori_100_|使用不可|  
|マプ語 (チリ)|Mapudungan_100_|使用不可|  
|マラーティー語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|モホーク語 (カナダ)|Mohawk_100_|使用不可|  
|モンゴル語 (PRC)|Cyrillic_General_100_|使用不可|  
|ネパール語 (ネパール)|Nepali_100_<sup>1</sup>|使用不可|  
|ノルウェー語 (ブークモール、ノルウェー)|Norwegian_100_|使用不可|  
|ノルウェー語 (ニーノシュク、ノルウェー)|Norwegian_100_|使用不可|  
|オクシタン語 (フランス)|French_100_|使用不可|  
|オリヤー語 (インド)|Indic_General_100_<sup>1</sup>|使用不可|  
|パシュトゥー語 (アフガニスタン)|Pashto_100_<sup>1</sup>|使用不可|  
|ペルシア語 (イラン)|Persian_100_|使用不可|  
|パンジャーブ語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|ケチュア語 (ボリビア)|Latin1_General_100_|使用不可|  
|ケチュア語 (エクアドル)|Latin1_General_100_|使用不可|  
|ケチュア語 (ペルー)|Latin1_General_100_|使用不可|  
|ロマンシュ語 (スイス)|Romansh_100_|使用不可|  
|サーミ語 (イナリ、フィンランド)|Sami_Sweden_Finland_100_|使用不可|  
|サーミ語 (ルレ、ノルウェー)|Sami_Norway_100_|使用不可|  
|サーミ語 (ルレ、スウェーデン)|Sami_Sweden_Finland_100_|使用不可|  
|サーミ語 (北、フィンランド)|Sami_Sweden_Finland_100_|使用不可|  
|サーミ語 (北、ノルウェー)|Sami_Norway_100_|使用不可|  
|サーミ語 (北、スウェーデン)|Sami_Sweden_Finland_100_|使用不可|  
|サーミ語 (スコルト、フィンランド)|Sami_Sweden_Finland_100_|使用不可|  
|サーミ語 (南、ノルウェー)|Sami_Norway_100_|使用不可|  
|サーミ語 (南、スウェーデン)|Sami_Sweden_Finland_100_|使用不可|  
|サンスクリット語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|セルビア語 (ボスニア・ヘルツェゴビナ、キリル文字)|Serbian_Cyrillic_100_|使用不可|  
|セルビア語 (ボスニア・ヘルツェゴビナ、ラテン文字)|Serbian_Latin_100_|使用不可|  
|セルビア語 (セルビア、キリル文字)|Serbian_Cyrillic_100_|使用不可|  
|セルビア語 (セルビア、ラテン文字)|Serbian_Latin_100_|使用不可|  
|セソト サ レボア語/北ソト語 (南アフリカ)|Latin1_General_100_|使用不可|  
|セツワナ語/ツワナ語 (南アフリカ)|Latin1_General_100_|使用不可|  
|シンハラ語 (スリランカ)|Indic_General_100_<sup>1</sup>|使用不可|  
|スワヒリ語 (ケニア)|Latin1_General_100_|使用不可|  
|シリア語 (シリア)|Syriac_100_<sup>1</sup>|Syriac_90_|  
|タジク語 (タジキスタン)|Cyrillic_General_100_|使用不可|  
|タマジット語 (アルジェリア、ラテン文字)|Tamazight_100_|使用不可|  
|タミール語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|テルグ語 (インド)|Indic_General_100_<sup>1</sup>|Indic_General_90_|  
|チベット語 (PRC)|Tibetan_100_<sup>1</sup>|使用不可|  
|トルクメン語 (トルクメニスタン)|Turkmen_100_|使用不可|  
|ウイグル語 (PRC)|Uighur_100_|使用不可|  
|上ソルブ語 (ドイツ)|Upper_Sorbian_100_|使用不可|  
|ウルドゥー語 (パキスタン)|Urdu_100_|使用不可|  
|ウェールズ語 (イギリス)|Welsh_100_|使用不可|  
|ウォロフ語 (セネガル)|French_100_|使用不可|  
|コサ語 (南アフリカ)|Latin1_General_100_|使用不可|  
|ヤクート語 (ロシア)|Yakut_100_|使用不可|  
|イ語 (PRC)|Latin1_General_100_|使用不可|  
|ヨルバ語 (ナイジェリア)|Latin1_General_100_|使用不可|  
|ズールー語 (南アフリカ)|Latin1_General_100_|使用不可|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では非推奨であり、サーバー レベルでは利用できません|ヒンディー語|ヒンディー語|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では非推奨であり、サーバー レベルでは利用できません|Korean_Wansung_Unicode|Korean_Wansung_Unicode|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では非推奨であり、サーバー レベルでは利用できません|Lithuanian_Classic|Lithuanian_Classic|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では非推奨であり、サーバー レベルでは利用できません|Macedonian|Macedonian|  
  
 <sup>1</sup> Unicode 専用の Windows 照合順序は、列レベルまたは式レベルのデータにのみ適用できます。 これらの照合順序は、サーバーまたはデータベースの照合順序としては使用できません。  
  
 <sup>2</sup> 中国語 (台湾) の照合順序と同様に、中国語 (マカオ) は簡体中国語の規則を使用し、中国語 (台湾) とは異なるコード ページ 950 を使用します。  
  
## <a name="see-also"></a>参照  
 [照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [定数 &#40;Transact-SQL&#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [テーブル &#40;Transact-SQL&#41;](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  
