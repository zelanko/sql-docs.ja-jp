---
title: ICommandWithParameters |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: edcba0cfc8ca284fd046f787829af4ba73dd366b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177736"
---
# <a name="icommandwithparameters"></a>ICommandWithParameters
  データベース エンジンが始まるの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]期待される結果のより正確な記述を取得するには、icommandwithparameters::getparameterinfo を許可します。 以前のバージョンの CommandWithParameters::GetParameterInfo によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../native-client/features/metadata-discovery.md)です。  
  
 以降ではまた[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]に渡された値、icommandwithparameters::setparameterinfo を呼び出すときに、 *pwszName*パラメーターは、有効な識別子である必要があります。 詳細については、「[データベース識別子](../databases/database-identifiers.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  