---
title: ICommandWithParameters | Microsoft Docs
description: ICommandWithParameters インターフェイス
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 205a93fe5ce57a8b4c10fffb8648a1ef4c7b6506
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015462"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降のデータベース エンジンの機能強化により、ICommandWithParameters::GetParameterInfo で、期待される結果のより正確な記述を取得できるようになりました。 結果がより正確になり、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で CommandWithParameters::GetParameterInfo から返される値とは異なる可能性があります。 詳細については、「[メタデータの検出](../../oledb/features/metadata-discovery.md)」を参照してください。  
  
 また、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降で、ICommandWithParameters::SetParameterInfo を呼び出す際、*pwszName* パラメーターに渡される値は有効な識別子である必要があります。 詳細については、「[データベース識別子](../../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
