---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
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
# <a name="collation-functions---collationproperty-transact-sql"></a>照合順序関数 - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で指定された照合順序のプロパティを返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>引数  
*collation_name*  
照合順序の名前を指定します。 collation_name *は nvarchar (128)*, 、既定値はありません。
  
*property*  
照合順序のプロパティを指定します。 プロパティ *は varchar (128)*, 、次の値のいずれかを指定できます。
  
|プロパティ名|Description|  
|---|---|
|**CodePage**|照合順序の Unicode 以外のコード ページ。 これらの値を変換してその文字マッピングを確認するには、「[Appendix G Mapping Tables](https://msdn.microsoft.com/en-us/library/cc194886.aspx)」(付録G: DBCS/Unicode マッピングテーブル) と「[Appendix H Code Pages](https://msdn.microsoft.com/en-us/library/cc195051.aspx)」(付録H: コード ページ) を参照してください。|  
|**LCID**|照合順序の Windows LCID。 これらの値を変換するには、「[LCID Structure](https://msdn.microsoft.com/en-us/library/cc233968.aspx)」(LCID 構造) を参照してください (最初に **varbinary** に変換する必要があります)。|  
|**ComparisonStyle**|照合順序の Windows 比較形式。 (\_BIN) と (\_BIN2) の両方と、すべてのプロパティに区別がある場合、すべてのバイナリ照合順序に対して 0 を返します。 ビットマスク値:<br /><br /> 大文字と小文字を区別しない: 1<br /><br /> アクセントを無視する: 2<br /><br /> ひらがなとカタカナを区別しない: 65536<br /><br /> 全角と半角を区別しない: 131072<br /><br /> 注: 比較動作に影響する場合でも、variation-selector-sensitive (\_VSS) オプションはこの値では表されません。|  
|**[バージョン]**|照合順序 ID のバージョン フィールドから継承した照合順序のバージョン。 0 ～ 3 の整数値を返します。<br /><br /> 名前に "140" が含まれる照合順序では、3 が返されます。<br /><br /> 名前に "100" が含まれる照合順序では、2 が返されます。<br /><br /> 名前に "90" が含まれる照合順序では、1 が返されます。<br /><br /> 他のすべての照合順序では 0 が返されます。|  
  
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
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>参照
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

