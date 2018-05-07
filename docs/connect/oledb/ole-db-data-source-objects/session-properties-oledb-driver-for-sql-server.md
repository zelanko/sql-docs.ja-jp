---
title: セッションのプロパティ - OLE DB Driver for SQL Server |Microsoft ドキュメント
description: セッションのプロパティ - OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3a6c4816c57ea0cac07f17a34e1dfafa1d4b2e93
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>セッションのプロパティ - OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server では、OLE DB セッション プロパティを次のように解釈されます。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|SQL Server の OLE DB Driver は、カオス レベル DBPROPVAL_TI_CHAOS を除くすべての自動コミット トランザクション分離レベルをサポートします。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERSESSION では、SQL Server の OLE DB Driver は、次の追加のセッション プロパティを定義します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|型 : VT_BOOL<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : CATALOG 制約で、引用符で囲まれた識別子を許可するかどうかを指定します。<br /><br /> VARIANT_TRUE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されます。<br /><br /> VARIANT_FALSE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されません。<br /><br /> 分散クエリをサポートするスキーマ行セットの詳細については、次を参照してください。[分散クエリのスキーマ行セットでサポート](../../oledb/ole-db/schema-rowsets-distributed-query-support.md)です。|  
|SSPROP_ALLOWNATIVEVARIANT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。<br /><br /> VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。<br /><br /> VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。|  
|SSPROP_ASYNCH_BULKCOPY|非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定してから、BCPExec メソッドを呼び出します。 このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
