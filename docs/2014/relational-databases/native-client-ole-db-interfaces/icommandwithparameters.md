---
title: ICommandWithParameters |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea85e526d99e586c2534eee8ab83c6ddc66939db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62643254"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  ICommandWithParameters:: GetParameterInfo で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]始まるデータベースエンジンの機能強化により、予想される結果についてより正確な説明を取得できます。 これらのより正確な結果は、以前のバージョンのの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CommandWithParameters:: getparameterinfo によって返される値とは異なる場合があります。 詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。  
  
 また、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降で、ICommandWithParameters::SetParameterInfo を呼び出す際、*pwszName* パラメーターに渡される値は有効な識別子である必要があります。 詳細については、「[データベース識別子](../databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
