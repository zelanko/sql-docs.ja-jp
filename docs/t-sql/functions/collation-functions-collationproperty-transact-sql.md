---
title: "COLLATIONPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f47c45f892618120b06a17f45f5d3155e092987a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="collation-functions---collationproperty-transact-sql"></a>照合順序関数、COLLATIONPROPERTY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定された照合順序のプロパティを返します[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>引数  
*collation_name*  
照合順序の名前を指定します。 *collation_name*は**nvarchar (128)**、既定値はありません。
  
*プロパティ*  
照合順序のプロパティを指定します。 *プロパティ*は**varchar (128)**、次の値のいずれかを指定できます。
  
|プロパティ名|Description|  
|---|---|
|**CodePage**|照合順序の Unicode 以外のコード ページ。 参照してください[付録 G DBCS/Unicode マッピング テーブル](https://msdn.microsoft.com/en-us/library/cc194886.aspx)と[付録 H コード ページ](https://msdn.microsoft.com/en-us/library/cc195051.aspx)をこれらの値を変換し、その文字マッピングを参照してください。|  
|**LCID**|照合順序の Windows LCID。 参照してください[LCID 構造](https://msdn.microsoft.com/en-us/library/cc233968.aspx)これらの値を変換する (に変換する必要があります**varbinary**最初)。|  
|**ComparisonStyle**|照合順序の Windows 比較形式。 すべてのバイナリ照合順序は 0 を返します両方 (\_BIN) と (\_BIN2)、およびすべてのプロパティが機密性の高い場合。 ビットマスク値を指定します。<br /><br /> 大文字小文字を区別します 1。<br /><br /> アクセントを区別しない: 2<br /><br /> ひらがなとカタカナ: 65536<br /><br /> 幅を無視: 131072<br /><br /> 注: いなくても、動作に影響の比較、バリエーション セレクター機密データ (\_VSS) オプションは、この値では表されません。|  
|**バージョン**|照合順序 ID のバージョン フィールドから継承した照合順序のバージョン。 0 ~ 3 の範囲の整数値を返します。<br /><br /> 照合順序名に「140」では、3 を返します。<br /><br /> 名前に「100」との照合順序は、2 を返します。<br /><br /> 名前に「90」照合順序は、1 を返します。<br /><br /> 他のすべての照合順序では 0 が返されます。|  
  
## <a name="return-types"></a>戻り値の型
**sql_variant**
  
## <a name="examples"></a>使用例  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]そして[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>参照
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

