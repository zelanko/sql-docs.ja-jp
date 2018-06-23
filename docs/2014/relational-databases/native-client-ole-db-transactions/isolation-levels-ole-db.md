---
title: 分離レベル (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6a83ec8d81a3c9e07c36c3973735c3a62746bd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177081"
---
# <a name="isolation-levels-ole-db"></a>分離レベル (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントは、接続のトランザクション分離レベルを制御できます。 トランザクション分離レベルを制御する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが使用します。  
  
-   DBPROPSET_SESSION プロパティの DBPROP_SESS_AUTOCOMMITISOLEVELS を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの既定の自動コミット モードです。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの既定のレベルは、DBPROPVAL_TI_READCOMMITTED です。  
  
-   *IsoLevel*のパラメーター、 **itransactionlocal::starttransaction**手動コミット トランザクションのローカルのメソッドです。  
  
-   *IsoLevel*のパラメーター、 **itransactiondispenser::begintransaction**メソッドの MS DTC によってコーディネートされる分散トランザクションです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ダーティ リード分離レベルでの読み取り専用アクセスを許可します。 他のすべてのレベルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトにロックをかけることによって同時実行を制限します。 クライアントがより高度な同時実行レベルを要求すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータへの同時アクセスに対してより厳密な制限を適用します。 最高レベルのデータへの同時アクセスを維持するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーは、特定の同時実行レベルの要求を適切に制御する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではスナップショット分離レベルが導入されました。 詳細については、次を参照してください。[スナップショット分離を使用した作業](../native-client/features/working-with-snapshot-isolation.md)です。  
  
## <a name="see-also"></a>参照  
 [トランザクション](transactions.md)  
  
  