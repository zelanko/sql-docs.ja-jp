---
title: プロジェクトの設定 (型のマッピング) (OracleToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 84d47276324b7616a30aff3d14949230595194c4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="project-settings-type-mapping-oracletosql"></a>プロジェクトの設定 (型のマッピング) (OracleToSQL)
[型マッピング] ページ、**プロジェクト設定** ダイアログ ボックスには、SSMA に Oracle データ型に変換する方法をカスタマイズする設定が含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型。  
  
型マッピング ページがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   今後のすべての SSMA プロジェクトの設定を指定する、**ツール**ボタンをクリックし**プロジェクト設定の既定の**、設定は表示または変更に必要な移行プロジェクトの種類を選択**移行のターゲット バージョン**ドロップダウンをクリックし、**の種類のマッピング**左側のウィンドウの下部にあります。  
  
-   現在のプロジェクトの設定を指定する、**ツール**ボタンをクリックし**プロジェクト設定**、順にクリック**型マッピング**左側のウィンドウの下部にあります。  
  
現在のオブジェクトまたはオブジェクトのクラスの設定を指定する、**型マッピング**プライマリ SSMA ウィンドウでタブです。  
  
## <a name="options"></a>オプション  
次の表に、**型マッピング**タブのオプション。  
  
**変換元の型**  
マップされた Oracle データ型。  
  
**ターゲットの種類**  
ターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]指定の Oracle データ型のデータ型。  
  
SSMA Oracle 型のマッピングの既定の値については、次のセクション内のテーブルを参照してください。  
  
**[追加]**  
マッピングのリストに、データ型を追加する をクリックします。  
  
**[編集]**  
マッピングの一覧で選択したデータ型を編集する をクリックします。  
  
**[削除]**  
マッピングのリストから選択したデータ型のマッピングを削除する をクリックします。  
  
**既定値にリセット**  
SSMA の既定値に型マッピングのリストをリセットする をクリックします。  
  
## <a name="default-type-mappings"></a>既定の型マッピング  
SSMA for Oracle には、引数、列、ローカル変数、および戻り値のカスタム型マッピングを設定できます。 引数と戻り値の型の既定のマッピングはほぼ同じです。  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>既定の引数の型と値の型マッピングを返します  
次の表には、引数と戻り値の既定のデータ型マッピングが含まれています。  
  
|Oracle データ型|既定の[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_integer|int|  
|blob (blob)|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|Clob|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec [38] [0]|  
|decimal|float [53]|  
|倍精度|float [53]|  
|float|float [53]|  
|int|int|  
|整数 (integer)|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [\*..8000]<sup>*</sup>|varbinary [*]|  
|long raw [8001..\*]<sup>*</sup>|varbinary(max)|  
|national char|nvarchar(max)|  
|varying、national char|nvarchar(max)|  
|各国語文字|nvarchar(max)|  
|各国語文字 varying<sup>**</sup>|nvarchar(max)|  
|各国語文字 varying<sup>*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|Nclob|nvarchar(max)|  
|number|float [53]|  
|numeric|float [53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|int|  
|raw|varbinary(max)|  
|real|float [53]|  
|Rowid|uniqueidentifier|  
|signtype|smallint|  
|smallint|smallint|  
|string|varchar(max)|  
|timestamp|datetime2|  
|ローカルのタイム ゾーンのタイムスタンプ|datetimeoffset|  
|タイム ゾーンのタイムスタンプ|datetimeoffset|  
|Urowid|uniqueidentifier|  
|varchar|varchar(max)|  
|varchar2|varchar(max)|  
|xmltype|xml|  
  
<sup>*</sup> 値型のマッピングのみを返すに適用されます。  
  
<sup>**</sup> 引数の種類のマッピングのみに適用されます。  
  
### <a name="default-column-type-mapping"></a>既定の列の型マッピング  
次の表には、列の既定値の型のマッピングが含まれています。  
  
|Oracle データ型|既定の[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|blob (blob)|varbinary(max)|  
|char|char|  
|char のさまざまな [*..\*]|varchar [*]|  
|char [*..\*]|char [*]|  
|character|char|  
|文字がさまざまな [*..\*]|varchar [*]|  
|文字 [*..\*]|char [*]|  
|Clob|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec [38] [0]|  
|dec [*..\*]|dec [*] [0]|  
|dec [*..\*][\*..\*]|dec[*][\*]|  
|decimal|[38] [0] の 10 進数|  
|decimal [*..\*]|decimal [*] [0]|  
|decimal [*..\*][\*..\*]|decimal [*] [\*]|  
|倍精度|float [53]|  
|float|float [53]|  
|float [*..53]|float [*]|  
|float [54.. *]|float [53]|  
|int|int|  
|整数 (integer)|int|  
|long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*..8000]|varbinary [*]|  
|long raw [8001.. *]|varbinary(max)|  
|long varchar|varchar(max)|  
|長い [*..8000]|varchar [*]|  
|長い [8001.. *]|varchar(max)|  
|national char|NCHAR|  
|varying、national char [*..\*]|nvarchar [*]|  
|national char [*..\*]|nchar [*]|  
|各国語文字|NCHAR|  
|各国語文字 varying [*..\*]|nvarchar [*]|  
|各国語文字 [*..\*]|nchar [*]|  
|NCHAR|NCHAR|  
|nchar [*]|nchar [*]|  
|Nclob|nvarchar(max)|  
|number|float [53]|  
|数値 [*..\*]|数値 [*]|  
|数値 [*..\*][\*..\*]|数値 [*] [\*]|  
|numeric|numeric|  
|数値 [*..\*]|数値 [*]|  
|数値 [*..\*][\*..\*]|数値 [*] [\*]|  
|nvarchar2[*..\*]|nvarchar [*]|  
|生 [*..\*]|varbinary [*]|  
|real|float [53]|  
|Rowid|uniqueidentifier|  
|smallint|smallint|  
|timestamp|datetime2|  
|ローカルのタイム ゾーンのタイムスタンプ|datetimeoffset|  
|ローカルのタイム ゾーンのタイムスタンプ [*..\*]|datetimeoffset [*]|  
|タイム ゾーンのタイムスタンプ|datetimeoffset|  
|タイムスタンプのタイム ゾーン [*..\*]|datetimeoffset [*]|  
|タイムスタンプ [*..\*]|datetime2 [*]|  
|Urowid|uniqueidentifier|  
|urowid [*..\*]|uniqueidentifier|  
|varchar [*..\*]|varchar [*]|  
|varchar2 [*..\*]|varchar [*]|  
|Xmltype|xml|  
  
### <a name="default-local-variable-type-mapping"></a>既定のローカル変数の型マッピング  
次の表には、ローカル変数の既定値の型のマッピングが含まれています。  
  
|Oracle データ型|既定の[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_interger|int|  
|Blob|varbinary(max)|  
|ブール値|bit|  
|Char|char|  
|char のさまざまな [*..8000]|varchar [*]|  
|char のさまざまな [8001.. *]|varchar(max)|  
|char [*..8000]|char [*]|  
|char [8001.. *]|varchar(max)|  
|文字|char|  
|文字がさまざまな [*..8000]|varchar [*]|  
|文字がさまざまな [8001.. *]|varchar(max)|  
|文字 [*..8000]|char [*]|  
|文字 [8001.. *]|varchar(max)|  
|Clob|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec [38] [0]|  
|dec [*..\*]|dec [*] [0]|  
|dec [*..\*][\*..\*]|dec[*][\*]|  
|decimal|[38] [0] の 10 進数|  
|decimal [*..\*]|decimal [*] [0]|  
|decimal [*..\*][\*..\*]|decimal [*] [\*]|  
|倍精度|float [53]|  
|Float|float [53]|  
|float [*..53]|float [*]|  
|float [54.. *]|float [53]|  
|Int|int|  
|Integer|int|  
|整数 [*..\*]|数値 [*] [0]|  
|Long|varchar(max)|  
|long raw|varbinary(max)|  
|long raw [*..8000]|varbinary [*]|  
|long raw [8001.. *]|varbinary(max)|  
|national char|NCHAR|  
|varying、national char [*..4000]|nvarchar [*]|  
|varying、national char [4001.. *]|nvarchar(max)|  
|national char [*..4000]|nchar [*]|  
|national char [4001.. *]|nvarchar(max)|  
|各国語文字|NCHAR|  
|各国語文字 [*..4000]|nvarchar [*]|  
|各国語文字 [4001.. *]|nvarchar(max)|  
|各国語文字 varying [*..4000]|nvarchar [*]|  
|各国語文字 varying [4001.. *]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar [*..4000]|nchar [*]|  
|nchar [4001.. *]|nvarchar(max)|  
|nchar varying [*..4000]|nvarchar [*]|  
|nchar varying [4001.. *]|nvarchar(max)|  
|Nclob|nvarchar(max)|  
|数値|float [53]|  
|数値 [*..\*]|数値 [*]|  
|数値 [*..\*][\*..\*]|数値 [*] [\*]|  
|数値|数値 [38] [0]|  
|数値 [*..\*]|数値 [*]|  
|数値 [*..\*][\*..\*]|数値 [*] [\*]|  
|nvarchar2 [*..4000]|nvarchar [*]|  
|nvarchar2 [4001.. *]|nvarchar(max)|  
|pls_integer|int|  
|生 [*..8000]|varbinary [*]|  
|生 [8001.. *]|varbinary(max)|  
|Real|float [53]|  
|Rowid|uniqueidentifier|  
|Signtype|smallint|  
|Smallint|smallint|  
|文字列 [*..8000]|varchar [*]|  
|文字列 [8001.. *]|varchar(max)|  
|timestamp|datetime2|  
|ローカルのタイム ゾーンのタイムスタンプ|datetimeoffset|  
|タイム ゾーンのタイムスタンプ|datetimeoffset|  
|ローカルのタイム ゾーンのタイムスタンプ [*..\*]|datetimeoffset [*]|  
|タイムスタンプのタイム ゾーン [*..\*]|datetimeoffset [*]|  
|タイムスタンプ [*..\*]|datetime2 [*]|  
|Urowid|uniqueidentifier|  
|urowid [*..\*]|uniqueidentifier|  
|varchar [*..8000]|varchar [*]|  
|varchar [8001.. *]|varchar(max)|  
|varchar2 [*..8000]|varchar [*]|  
|varchar2 [8001.. *]|varcha(max)|  
|Xmltype|xml|  
  
## <a name="see-also"></a>参照  
[ユーザー インターフェイス リファレンス&#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
