---
title: 分離レベル (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec099f18afd80bd07f059d3e87b18598b36b1117
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420727"
---
# <a name="isolation-levels-ole-db"></a>分離レベル (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントは、接続のトランザクション分離レベルを制御できます。 トランザクション分離レベルを制御する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーの使用。  
  
-   DBPROPSET_SESSION プロパティの DBPROP_SESS_AUTOCOMMITISOLEVELS を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの既定の自動コミット モード。  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの既定のレベルは、DBPROPVAL_TI_READCOMMITTED です。  
  
-   *IsoLevel*のパラメーター、 **itransactionlocal::starttransaction**手動コミット トランザクションをローカルのメソッド。  
  
-   *IsoLevel*のパラメーター、 **itransactiondispenser::begintransaction**メソッドの MS DTC によってコーディネートされる分散トランザクション。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ダーティ リード分離レベルでの読み取り専用アクセスを許可します。 他のすべてのレベルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトにロックをかけることによって同時実行を制限します。 クライアントがより高度な同時実行レベルを要求すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータへの同時アクセスに対してより厳密な制限を適用します。 最高レベルのデータへの同時アクセスを維持するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーがその要求の特定の同時実行レベルを適切に制御する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではスナップショット分離レベルが導入されました。 詳細については、次を参照してください。[スナップショット分離を使用した作業](../native-client/features/working-with-snapshot-isolation.md)します。  
  
## <a name="see-also"></a>参照  
 [トランザクション](transactions.md)  
  
  
