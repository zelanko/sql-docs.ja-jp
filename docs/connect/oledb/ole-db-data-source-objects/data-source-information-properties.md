---
title: データ ソースの情報のプロパティ |Microsoft Docs
description: データ ソース情報のプロパティ
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 06a6f4152876f123d1e7fc7ecaf009061d10aa59
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031955"
---
# <a name="data-source-information-properties"></a>データ ソース情報のプロパティ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCEINFO には、OLE DB Driver for SQL Server により、次のデータ ソース情報のプロパティが定義されます。  
  
|プロパティ ID|[説明]|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|型 : VT_BOOL<br /><br /> R/W: 読み取り<br /><br /> 既定値 : VARIANT_TRUE<br /><br /> 説明 : 列の照合順序がサポートされるかどうかの判断に使用されます。<br /><br /> VARIANT_TRUE: 列レベルの照合順序がサポートされます。<br /><br /> VARIANT_FALSE: 列レベルの照合順序はサポートされません。|  
|SSPROP_UNICODELCID|型 : VT_I4 R/W: 読み取り<br /><br /> 説明 : Unicode ロケール ID です。<br /><br /> これは、Unicode データの並べ替えに使われるロケールです。|  
|SSPROP_UNICODECOMPARISONSTYLE|型 : VT_I4 R/W: 読み取り<br /><br /> 説明 : Unicode 比較形式です。<br /><br /> Unicode データの並べ替えに使われる並べ替えオプションです。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERSTREAM には、OLE DB Driver for SQL Server により、次の追加プロパティが定義されます。  
  
|プロパティ ID|[説明]|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|型 : VT_BSTR R/W: 読み取り/書き込み<br /><br /> 説明: FOR XML クエリの結果に、整形式でないドキュメントを許可します。 このプロパティが指定されている場合の結果を ' を選択しています. for XML' クエリが、整形式 XML ドキュメントを返すためには、このプロパティによって提供されるルート タグにラップされています。 クエリがブラウザーから実行されている場合、結果の読み込み時にブラウザーがパーサー エラーを表示する場合があります。 このエラーを回避するために、SQL ISAPI はキーワード ROOT をサポートしています。 このキーワードは SSPROP_STREAM_XMLROOT プロパティにマップされます。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト&#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
