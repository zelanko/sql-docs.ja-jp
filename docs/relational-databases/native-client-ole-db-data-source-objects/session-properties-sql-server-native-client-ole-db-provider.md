---
title: セッションのプロパティ - SQL Server Native Client OLE DB プロバイダー |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d17b673a12a915318e523000081fcd6114e8185c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128547"
---
# <a name="session-properties---sql-server-native-client-ole-db-provider"></a>セッション プロパティ - SQL Server Native Client OLE DB プロバイダー
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが OLE DB セッションのプロパティを次のように解釈します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、カオス レベル DBPROPVAL_TI_CHAOS を除くすべての自動コミット トランザクション分離レベルをサポートしています。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERSESSION には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次の追加のセッション プロパティを定義します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|型:VT_BOOL<br /><br /> R/W読み取り/書き込み<br /><br /> 既定値:VARIANT_FALSE<br /><br /> 説明:引用符付き識別子のカタログ制約で許可します。<br /><br /> VARIANT_TRUE:分散クエリをサポートするスキーマ行セットのカタログ制約は、引用符で囲まれた識別子が認識します。<br /><br /> VARIANT_FALSE:引用符で囲まれた識別子は、分散クエリをサポートするスキーマ行セットのカタログの制限については認識されません。<br /><br /> 分散クエリをサポートするスキーマ行セットの詳細については、「[スキーマ行セットでの分散クエリのサポート](../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md)」を参照してください。|  
|SSPROP_ALLOWNATIVEVARIANT|型:VT_BOOL<br /><br /> R/W[読み取り/書き込み]<br /><br /> 既定値:VARIANT_FALSE<br /><br /> 説明:フェッチされるデータを DBTYPE_VARIANT と dbtype_sqlvariant のどちらとしてかどうかを判断します。<br /><br /> VARIANT_TRUE:列の型は、SSVARIANT 構造体をバッファーが保持されます DBTYPE_SQLVARIANT として返されます。<br /><br /> VARIANT_FALSE:列の型は DBTYPE_VARIANT として返されます、バッファーは VARIANT 構造体に必要があります。|  
|SSPROP_ASYNCH_BULKCOPY|非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定してから、BCPExec メソッドを呼び出します。 このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。|  
  
## <a name="see-also"></a>関連項目  
 [データ ソース オブジェクト&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
