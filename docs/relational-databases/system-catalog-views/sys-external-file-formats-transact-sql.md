---
title: sys.external_file_formats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f834434e2e03bad82df9221b1d66db6f4f1e300a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38059129"
---
# <a name="sysexternalfileformats-transact-sql"></a>sys.external_file_formats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  1 行の現在のデータベースでは、各外部ファイル形式のデータを含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、および[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。  
  
 サーバーの場合は、各外部ファイル形式の行を格納[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|外部のファイル形式のオブジェクト ID。||  
|NAME|**sysname**|ファイル形式の名前です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、これは、データベースに一意です。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、これは、サーバーに一意です。||  
|format_type|**tinyint**|ファイル形式の種類。|DELIMITEDTEXT、RCFILE、ORC、PARQUET|  
|field_terminator|**nvarchar(10)**|Format_type = DELIMITEDTEXT、フィールド ターミネータです。||  
|string_delimiter|**nvarchar(10)**|Format_type = DELIMITEDTEXT、これは、文字列の区切り記号です。||  
|date_format|**nvarchar (50)**|Format_type = DELIMITEDTEXT、これは、ユーザー定義の日付と時刻の形式です。||  
|use_type_default|**bit**|Format_type = 区切りのテキスト、PolyBase にテキスト ファイルを HDFS からデータをインポートするときに、欠損値を処理する方法を指定します[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。|0 ～ は、文字列の 'NULL' として、不足値を格納します。<br /><br /> 1 – 列の既定値として、不足値を格納します。|  
|serde_method|**nvarchar (255)**|Format_type = RCFILE、これは、シリアル化/逆シリアル化メソッドです。||  
|row_terminator|**nvarchar(10)**|Format_type = DELIMITEDTEXT、これは、外部の Hadoop ファイル内の各行の終了文字を指定します。|常に ' \n' です。|  
|エンコーディング|**nvarchar(10)**|Format_type = DELIMITEDTEXT、これは、外部の Hadoop ファイルのエンコード方法です。|常に ' UTF8' とします。|  
|data_compression|**nvarchar (255)**|外部データのデータ圧縮方法。|Format_type = DELIMITEDTEXT に。<br /><br /> -'org.apache.hadoop.io.compress.defaultcodec'<br />-'org.apache.hadoop.io.compress.gzipcodec'<br /><br /> Format_type RCFILE を = します。<br /><br /> -'org.apache.hadoop.io.compress.defaultcodec'<br /><br /> Format_type = ORC:<br /><br /> -'org.apache.hadoop.io.compress.defaultcodec'<br />-'org.apache.hadoop.io.compress.snappycodec'<br /><br /> Format_type = PARQUET:<br /><br /> -'org.apache.hadoop.io.compress.gzipcodec'<br />-'org.apache.hadoop.io.compress.snappycodec'|  
  
## <a name="permissions"></a>アクセス許可  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.external_data_sources &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [sys.external_tables &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
