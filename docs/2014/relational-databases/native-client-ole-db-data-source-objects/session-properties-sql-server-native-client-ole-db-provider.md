---
title: セッションのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6a26faf8673ff110e079d4606e587e079f33025
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413361"
---
# <a name="session-properties"></a>セッション プロパティ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが OLE DB セッションのプロパティを次のように解釈します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、カオス レベル DBPROPVAL_TI_CHAOS を除くすべての自動コミット トランザクション分離レベルをサポートしています。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERSESSION には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次の追加のセッション プロパティを定義します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|型 : VT_BOOL<br /><br /> R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : CATALOG 制約で、引用符で囲まれた識別子を許可するかどうかを指定します。<br /><br /> VARIANT_TRUE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されます。<br /><br /> VARIANT_FALSE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されません。<br /><br /> 分散クエリをサポートするスキーマ行セットの詳細については、次を参照してください。[スキーマ行セットで分散クエリのサポート](../native-client/ole-db/schema-rowsets-distributed-query-support.md)します。|  
|SSPROP_ALLOWNATIVEVARIANT|型 : VT_BOOL<br /><br /> R/W: 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。<br /><br /> VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。<br /><br /> VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。|  
|SSPROP_ASYNCH_BULKCOPY|非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定してから、BCPExec メソッドを呼び出します。 このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト&#40;OLE DB&#41;](data-source-objects-ole-db.md)  
  
  
