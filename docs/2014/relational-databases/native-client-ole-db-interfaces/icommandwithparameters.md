---
title: ICommandWithParameters |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c43b41faa03ae9838cc0dcec619179d272f238e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408152"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  データベース エンジンが以降の機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]期待どおりの結果のより正確な記述を取得するには、icommandwithparameters::getparameterinfo を許可します。 これらのより正確な結果の以前のバージョンの CommandWithParameters::GetParameterInfo によって返される値が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 詳細については、次を参照してください。[メタデータ検出](../native-client/features/metadata-discovery.md)します。  
  
 以降ではまた[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]に渡される値、icommandwithparameters::setparameterinfo を呼び出すときに、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、「[データベース識別子](../databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
