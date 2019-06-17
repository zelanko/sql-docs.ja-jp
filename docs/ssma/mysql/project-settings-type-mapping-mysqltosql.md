---
title: プロジェクトの設定 (型のマッピング) (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e0a11a0b49589c3763b5af67623c9e819038c217
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63231819"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>プロジェクトの設定 (型のマッピング) (MySQLToSQL)
プロジェクトの型マッピングの設定では、SSMA プロジェクトの既定の型マッピングを設定できます。  

型のマッピングは、プロジェクトの設定とプロジェクトの既定の設定 ダイアログ ボックスで利用できます。  
  
-   プロジェクトの設定 ダイアログ ボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 型のマッピング設定の ツール メニューにアクセスするには、プロジェクトの設定 を選択し、左側のウィンドウで型のマッピングをクリックします。  
  
-   プロジェクトの既定の設定 ダイアログ ボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 ツール メニューの設定を型のマッピングにアクセスするには、既定のプロジェクトの設定、移行プロジェクトの種類の設定は、表示/から変更する必要を選択します**移行ターゲット バージョン**ドロップダウンをクリックしての種類左側のウィンドウでマッピングします。  
  
## <a name="options"></a>および  
  
##### <a name="source-type"></a>[変換元の型]  
ターゲット データベースのデータ型にマップする必要がある MySQL のデータ型になります。  
  
##### <a name="target-type"></a>ターゲットの種類  
ターゲット データベースのデータは、指定の MySQL のデータ型の型します。  
  
##### <a name="add"></a>[追加]  
データ型をマッピングの一覧に追加する をクリックします。  
  
##### <a name="edit"></a>編集  
マッピングの一覧で選択したデータ型を編集する をクリックします。  
  
##### <a name="remove"></a>[削除]  
マッピングの一覧から選択したデータ型のマッピングを削除する をクリックします。  
  
##### <a name="reset-to-default"></a>[既定値にリセット]  
SSMA の既定値に型マッピングのリストをリセットする をクリックします。  
  
## <a name="type-mappings"></a>型のマッピング  
次の表は、ソースとターゲットのデータ型の既定のマッピングを示しています。  
  
|||  
|-|-|  
|**MySQL のデータ型**|**SQL Server データ型**|  
|BIGINT|BIGINT|  
|bigint [*..255]|BIGINT|  
|binary|バイナリ [1]|  
|バイナリ [0..1]|バイナリ [1]|  
|バイナリ [2..255]|バイナリ [*]|  
|bit|バイナリ [1]|  
|bit[0..8]|バイナリ [1]|  
|ビット [17..24]|バイナリ [3]|  
|ビット [25..32]|バイナリ [4]|  
|bit[33..40]|バイナリ [5]|  
|ビット [41..48]|binary[6]|  
|bit[49..56]|binary[7]|  
|ビット [57..64]|binary[8]|  
|bit[9..16]|バイナリ [2]|  
|blob (blob)|varbinary(max)|  
|blob[0..1]|varbinary[1]|  
|blob[2..8000]|varbinary[*]|  
|blob [8001.. *]|varbinary(max)|  
|[bool]|bit|  
|boolean|bit|  
|char|nchar [1]|  
|char バイト|バイナリ [1]|  
|char byte[0..1]|バイナリ [1]|  
|バイト [2..255] char 型します。|バイナリ [*]|  
|char[0..1]|nchar [1]|  
|char [2..255]|nchar[*]|  
|character|nchar [1]|  
|文字のさまざまな [0..1]|nvarchar [1]|  
|文字のさまざまな [2..255]|NVARCHAR|  
|文字 [0..1]|nchar [1]|  
|文字 [2..255]|nchar[*]|  
|日付|日付|  
|DATETIME|datetime2 [0]|  
|dec|Decimal|  
|dec [*..65]|10 進数 [*] [0]|  
|dec [*..65] [\*..30]|decimal[*][\*]|  
|Decimal|Decimal|  
|decimal [*..65]|10 進数 [*] [0]|  
|decimal [*..65] [\*..30]|decimal[*][\*]|  
|double|float [53]|  
|倍精度|float [53]|  
|倍精度 [*..255] [\*..30]|numeric[*][\*]|  
|二重 [*..255] [\*..30]|numeric[*][\*]|  
|修正しました|NUMERIC|  
|固定 [*..65] [\*..30]|numeric[*][\*]|  
|FLOAT|float [24]|  
|float [*..255] [\*..30]|numeric[*][\*]|  
|float [*..53]|float [53]|  
|ssNoversion|ssNoversion|  
|int [*..255]|ssNoversion|  
|整数 (integer)|ssNoversion|  
|整数 [*..255]|ssNoversion|  
|longblob|varbinary(max)|  
|長いテキスト|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|ssNoversion|  
|mediumint [*..255]|ssNoversion|  
|mediumtext|nvarchar(max)|  
|national char|nchar [1]|  
|national char [0..1]|nchar [1]|  
|national char [2..255]|nchar[*]|  
|各国語文字|nchar [1]|  
|各国語文字がさまざまな|nvarchar [1]|  
|各国語文字の可変 [0..1]|nvarchar [1]|  
|各国語文字の可変 [2..4000]|nvarchar [*]|  
|各国語文字がさまざまな [4001.. *]|nvarchar(max)|  
|各国語文字 [0..1]|nchar [1]|  
|各国語文字 [2..255]|nchar[*]|  
|national varchar|nvarchar [1]|  
|national varchar [0..1]|nvarchar [1]|  
|national varchar [2..4000]|nvarchar [*]|  
|national varchar [4001.. *]|nvarchar(max)|  
|NCHAR|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar[0..1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001.. *]|nvarchar(max)|  
|nchar[0..1]|nchar [1]|  
|nchar [2..255]|nchar[*]|  
|NUMERIC|NUMERIC|  
|数値 [*..65]|数値 [*] [0]|  
|数値 [*..65] [\*..30]|numeric[*][\*]|  
|NVARCHAR|nvarchar [1]|  
|nvarchar[0..1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar[4001..*]|nvarchar(max)|  
|REAL|float [53]|  
|実際 [*..255] [\*..30]|numeric[*][\*]|  
|シリアル|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*..255]|SMALLINT|  
|text|nvarchar(max)|  
|text[0..1]|nvarchar [1]|  
|text[2..4000]|nvarchar [*]|  
|text[4001..*]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|DATETIME|  
|tinyblob|varbinary [255]|  
|TINYINT|SMALLINT|  
|tinyint [*..255]|SMALLINT|  
|tinytext|nvarchar [255]|  
|unsigned bigint|BIGINT|  
|unsigned bigint[*..255]|BIGINT|  
|unsigned dec|Decimal|  
|符号なしの dec [*..65]|10 進数 [*] [0]|  
|符号なしの dec [*..65] [\*..30]|decimal[*][\*]|  
|unsigned decimal|Decimal|  
|符号なし 10 進数 [*..65]|10 進数 [*] [0]|  
|符号なし 10 進数 [*..65] [\*..30]|decimal[*][\*]|  
|倍精度浮動小数点符号なし|float [53]|  
|符号なしの倍精度|float [53]|  
|符号なしの倍精度 [*..255] [\*..30]|numeric[*][\*]|  
|符号なしの倍精度浮動小数点 [*..255] [\*..30]|numeric[*][\*]|  
|符号なしの固定|NUMERIC|  
|符号なしの固定 [*..65] [\*..30]|numeric[*][\*]|  
|符号なしの float|float [24]|  
|符号なしの float [*..255] [\*..30]|numeric[*][\*]|  
|符号なしの float [*..53]|float [53]|  
|unsigned int|BIGINT|  
|unsigned int[*..255]|BIGINT|  
|unsigned integer|BIGINT|  
|符号なし整数 [*..255]|BIGINT|  
|符号なしの mediumint|ssNoversion|  
|符号なしの mediumint [*..255]|ssNoversion|  
|unsigned numeric|NUMERIC|  
|unsigned numeric[*..65]|数値 [*] [0]|  
|unsigned numeric[*..65][\*..30]|numeric[*][\*]|  
|実際に符号なし|float [53]|  
|実際に署名されていない [*..255 [\*..30]|numeric[*][\*]|  
|unsigned smallint|ssNoversion|  
|符号なしの smallint [*..255]|ssNoversion|  
|unsigned tinyint|TINYINT|  
|符号なしの tinyint [*..255]|TINYINT|  
|varbinary[0..1]|varbinary[1]|  
|varbinary [2..8000]|varbinary[*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar[0..1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|year [2..2]|SMALLINT|  
|year [4..4]|SMALLINT|  
  
##### <a name="add"></a>[追加]  
データ型をマッピングの一覧に追加する をクリックします。  
  
##### <a name="edit"></a>編集  
データ型マッピングのリストを編集する をクリックします。  
  
##### <a name="remove"></a>[削除]  
マッピングの一覧から選択したデータ型のマッピングを削除する をクリックします。  
  
##### <a name="reset-to-default"></a>[既定値にリセット]  
すべてのデータ型マッピングを SSMA の既定値にリセットする をクリックします。  
  
