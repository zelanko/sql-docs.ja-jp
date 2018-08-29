---
title: 分離レベル (OLE DB) |Microsoft Docs
description: 分離レベル (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- isolation levels [OLE DB]
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 4bcb9de1cc0d09875dbe283b6ac8fe3cf46e883f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024778"
---
# <a name="isolation-levels-ole-db"></a>分離レベル (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアントは、接続のトランザクション分離レベルを制御できます。 トランザクション分離レベルを制御するには、OLE DB Driver for SQL Server コンシューマーが使用します。  
  
-   OLE DB Driver for SQL Server の既定の自動コミット モードには、DBPROPSET_SESSION プロパティの DBPROP_SESS_AUTOCOMMITISOLEVELS。  
  
     SQL Server の既定のレベルの OLE DB Driver は、DBPROPVAL_TI_READCOMMITTED です。  
  
-   ローカルの手動コミット トランザクションには、**ITransactionLocal::StartTransaction** メソッドの *isoLevel* パラメーター。  
  
-   MS DTC でコーディネートされる分散トランザクションには、**ITransactionDispenser::BeginTransaction** メソッドの *isoLevel* パラメーター。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、ダーティ リード分離レベルでの読み取り専用アクセスを許可します。 他のすべてのレベルでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクトにロックをかけることによって同時実行を制限します。 クライアントがより高度な同時実行レベルを要求すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はデータへの同時アクセスに対してより厳密な制限を適用します。 データへの最高レベルの同時アクセスを維持するには、OLE DB Driver for SQL Server のコンシューマーで、特定の同時実行レベルの要求を適切に制御する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ではスナップショット分離レベルが導入されました。 詳細については、「[スナップショット分離を使用した作業](../../oledb/features/working-with-snapshot-isolation.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [トランザクション](../../oledb/ole-db-transactions/transactions.md)  
  
  
