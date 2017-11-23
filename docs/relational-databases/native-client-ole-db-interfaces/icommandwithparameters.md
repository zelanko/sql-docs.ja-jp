---
title: "ICommandWithParameters |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 14eebf814d3dbcde2863e117814d3c8a07162945
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  データベース エンジンが始まるの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]期待される結果のより正確な記述を取得するには、icommandwithparameters::getparameterinfo を許可します。 以前のバージョンの CommandWithParameters::GetParameterInfo によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
 以降ではまた[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]に渡された値、icommandwithparameters::setparameterinfo を呼び出すときに、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
