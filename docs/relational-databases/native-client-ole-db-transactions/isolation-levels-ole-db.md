---
title: 分離レベル (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: d70ee72c-6e2a-4bcd-9456-4a697a866361
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c3535360e120e0f9c61a8cfb7cb578e531e92572
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280299"
---
# <a name="isolation-levels-ole-db"></a>分離レベル (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントは、接続のトランザクション分離レベルを制御できます。 トランザクション分離レベルを制御するために[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、Native Client OLE DB プロバイダーコンシューマーは次のものを使用します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの既定の自動コミットモードの DBPROPSET_SESSION プロパティ DBPROP_SESS_AUTOCOMMITISOLEVELS。  
  
     レベル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Native Client OLE DB プロバイダーの既定値は DBPROPVAL_TI_READCOMMITTED です。  
  
-   ローカルの手動コミット トランザクションには、**ITransactionLocal::StartTransaction** メソッドの *isoLevel* パラメーター。  
  
-   MS DTC でコーディネートされる分散トランザクションには、**ITransactionDispenser::BeginTransaction** メソッドの *isoLevel* パラメーター。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ダーティ リード分離レベルでの読み取り専用アクセスを許可します。 他のすべてのレベルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトにロックをかけることによってコンカレンシーを制限します。 クライアントがより高度なコンカレンシー レベルを要求すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータへのコンカレント アクセスに対してより厳密な制限を適用します。 データへの最大レベルの同時アクセスを維持するため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、Native Client OLE DB プロバイダーコンシューマーは、特定の同時実行レベルに対する要求をインテリジェントに制御する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではスナップショット分離レベルが導入されました。 詳細については、「[スナップショット分離を使用した作業](../../relational-databases/native-client/features/working-with-snapshot-isolation.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [トランザクション](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
