---
title: ICommandWithParameters |Microsoft ドキュメント
description: ICommandWithParameters インターフェイス
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 52f14f27b313db701108f537b126fa9321fab971
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  データベース エンジンが始まるの機能強化[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]期待される結果のより正確な記述を取得するには、icommandwithparameters::getparameterinfo を許可します。 以前のバージョンの CommandWithParameters::GetParameterInfo によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../oledb/features/metadata-discovery.md)です。  
  
 以降ではまた[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]に渡された値、icommandwithparameters::setparameterinfo を呼び出すときに、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、「[データベース識別子](../../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
