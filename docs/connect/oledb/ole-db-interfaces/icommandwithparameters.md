---
title: ICommandWithParameters |Microsoft Docs
description: ICommandWithParameters インターフェイス
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: a998292f4d1c03485dc75eee02cefa437dc1fe36
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600050"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  データベース エンジンが以降の機能強化[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]期待どおりの結果のより正確な記述を取得するには、icommandwithparameters::getparameterinfo を許可します。 これらのより正確な結果の以前のバージョンの CommandWithParameters::GetParameterInfo によって返される値が異なる場合があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 詳細については、次を参照してください。[メタデータ検出](../../oledb/features/metadata-discovery.md)します。  
  
 また、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降で、ICommandWithParameters::SetParameterInfo を呼び出す際、*pwszName* パラメーターに渡される値は有効な識別子である必要があります。 詳細については、「[データベース識別子](../../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
