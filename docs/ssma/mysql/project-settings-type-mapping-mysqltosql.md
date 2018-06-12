---
title: プロジェクトの設定 (型のマッピング) (MySQLToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9bf1d1c219b8673345d5f2074fe8885b5c58223f
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776778"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>プロジェクトの設定 (型のマッピング) (MySQLToSQL)
プロジェクトの種類のマッピング設定では、SSMA プロジェクトの既定の型マッピングを設定できます。  

型のマッピングは、プロジェクトの設定と既定のプロジェクト設定のダイアログ ボックスで入手できます。  
  
-   プロジェクトの設定 ダイアログ ボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 ツール メニューの種類のマッピングの設定にアクセスするには、プロジェクトの設定 を選択し、左側のウィンドウで 型のマッピング をクリックします。  
  
-   プロジェクトの既定の設定 ダイアログ ボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 ツール メニューの設定が既定のプロジェクトの設定、移行プロジェクトの種類の設定は、表示/からの変更にする必要を選択型のマッピングにアクセスする**移行のターゲット バージョン**ドロップダウンを 左側のウィンドウで型のマッピング をクリックします。  
  
## <a name="options"></a>および  
  
##### <a name="source-type"></a>[変換元の型]  
これは、ターゲット データベースのデータ型にマップする必要がある MySQL のデータ型です。  
  
##### <a name="target-type"></a>ターゲットの種類  
ターゲット データベースのデータは、指定された MySQL データ型の型します。  
  
##### <a name="add"></a>[追加]  
マッピングのリストに、データ型を追加する をクリックします。  
  
##### <a name="edit"></a>[編集]  
マッピングの一覧で選択したデータ型を編集する をクリックします。  
  
##### <a name="remove"></a>[削除]  
マッピングのリストから選択したデータ型のマッピングを削除する をクリックします。  
  
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
|ビット [0..8]|バイナリ [1]|  
|ビット [17..24]|バイナリ [3]|  
|ビット [25..32]|バイナリ [4]|  
|ビット [33..40]|バイナリ [5]|  
|ビット [41..48]|バイナリ [6]|  
|ビット [49..56]|バイナリ [7]|  
|ビット [57..64]|バイナリ [8]|  
|ビット [9..16]|[2]|  
|blob (blob)|varbinary(max)|  
|blob [0..1]|varbinary [1]|  
|blob[2..8000]|varbinary [*]|  
|blob [8001.. *]|varbinary(max)|  
|[bool]|bit|  
|boolean|bit|  
|char|nchar [1]|  
|char バイト|バイナリ [1]|  
|char バイト [0..1]|バイナリ [1]|  
|char バイト [2..255]|バイナリ [*]|  
|char [0..1]|nchar [1]|  
|char [2..255]|nchar [*]|  
|character|nchar [1]|  
|文字のさまざまな [0..1]|nvarchar [1]|  
|文字のさまざまな [2..255]|NVARCHAR|  
|文字 [0..1]|nchar [1]|  
|文字 [2..255]|nchar [*]|  
|日付|日付|  
|DATETIME|datetime2 [0]|  
|dec|Decimal|  
|dec [*..65]|decimal [*] [0]|  
|dec [*..65][\*..30]|decimal [*] [\*]|  
|Decimal|Decimal|  
|decimal [*..65]|decimal [*] [0]|  
|decimal [*..65][\*..30]|decimal [*] [\*]|  
|double|float [53]|  
|倍精度|float [53]|  
|倍精度 [*..255][\*..30]|数値 [*] [\*]|  
|二重 [*..255][\*..30]|数値 [*] [\*]|  
|固定|NUMERIC|  
|固定 [*..65][\*..30]|数値 [*] [\*]|  
|FLOAT|float [24]|  
|float [*..255][\*..30]|数値 [*] [\*]|  
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
|national char [2..255]|nchar [*]|  
|各国語文字|nchar [1]|  
|各国語文字 varying|nvarchar [1]|  
|各国語文字がさまざまな [0..1]|nvarchar [1]|  
|各国語文字がさまざまな [2..4000]|nvarchar [*]|  
|各国語文字 varying [4001.. *]|nvarchar(max)|  
|各国語文字 [0..1]|nchar [1]|  
|各国語文字 [2..255]|nchar [*]|  
|各国語 varchar|nvarchar [1]|  
|各国語 varchar [0..1]|nvarchar [1]|  
|各国語 varchar [2..4000]|nvarchar [*]|  
|各国語 varchar [4001.. *]|nvarchar(max)|  
|NCHAR|nchar [1]|  
|nchar varchar|nvarchar [1]|  
|nchar varchar [0..1]|nvarchar [1]|  
|nchar varchar [2..4000]|nvarchar [*]|  
|nchar varchar [4001.. *]|nvarchar(max)|  
|nchar [0..1]|nchar [1]|  
|nchar [2..255]|nchar [*]|  
|NUMERIC|NUMERIC|  
|数値 [*..65]|数値 [*] [0]|  
|数値 [*..65][\*..30]|数値 [*] [\*]|  
|NVARCHAR|nvarchar [1]|  
|nvarchar [0..1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|REAL|float [53]|  
|real [*..255][\*..30]|数値 [*] [\*]|  
|シリアル|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*..255]|SMALLINT|  
|text|nvarchar(max)|  
|テキスト [0..1]|nvarchar [1]|  
|text[2..4000]|nvarchar [*]|  
|テキスト [4001.. *]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|DATETIME|  
|tinyblob|varbinary [255]|  
|TINYINT|SMALLINT|  
|tinyint [*..255]|SMALLINT|  
|tinytext|nvarchar [255]|  
|符号なしの bigint|BIGINT|  
|符号なしの bigint [*..255]|BIGINT|  
|符号なし年 12 月|Decimal|  
|符号なし dec [*..65]|decimal [*] [0]|  
|符号なし dec [*..65][\*..30]|decimal [*] [\*]|  
|符号なし 10 進数|Decimal|  
|符号なし 10 進数 [*..65]|decimal [*] [0]|  
|符号なし 10 進数 [*..65][\*..30]|decimal [*] [\*]|  
|倍精度浮動小数点符号なし|float [53]|  
|符号なしの倍精度|float [53]|  
|倍精度を署名されていない [*..255][\*..30]|数値 [*] [\*]|  
|倍精度浮動小数点の符号なし [*..255][\*..30]|数値 [*] [\*]|  
|符号なし固定|NUMERIC|  
|符号なし固定 [*..65][\*..30]|数値 [*] [\*]|  
|符号なし float|float [24]|  
|符号なし float [*..255][\*..30]|数値 [*] [\*]|  
|符号なし float [*..53]|float [53]|  
|unsigned int|BIGINT|  
|符号なし int [*..255]|BIGINT|  
|符号なし整数|BIGINT|  
|符号なし整数 [*..255]|BIGINT|  
|符号なし mediumint|ssNoversion|  
|符号なし mediumint [*..255]|ssNoversion|  
|符号なし数値|NUMERIC|  
|符号なし数値 [*..65]|数値 [*] [0]|  
|符号なし数値 [*..65][\*..30]|数値 [*] [\*]|  
|実際の符号なし|float [53]|  
|実際の符号なし [*..255[[\*..30]|数値 [*] [\*]|  
|符号なし smallint|ssNoversion|  
|符号なし smallint [*..255]|ssNoversion|  
|符号なし tinyint|TINYINT|  
|符号なし tinyint [*..255]|TINYINT|  
|varbinary [0..1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [0..1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|year [2..2]|SMALLINT|  
|year [4..4]|SMALLINT|  
  
##### <a name="add"></a>[追加]  
マッピングのリストに、データ型を追加する をクリックします。  
  
##### <a name="edit"></a>[編集]  
マッピングのリスト内のデータ型を編集するのには、をクリックします。  
  
##### <a name="remove"></a>[削除]  
マッピングのリストから選択したデータ型のマッピングを削除する をクリックします。  
  
##### <a name="reset-to-default"></a>[既定値にリセット]  
すべてのデータ型マッピングを SSMA の既定値にリセットする をクリックします。  
  
