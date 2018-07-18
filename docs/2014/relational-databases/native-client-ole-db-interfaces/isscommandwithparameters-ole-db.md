---
title: ISSCommandWithParameters (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ceca46260d82cc6f9a179a642821aee55e57d6e3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429991"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
  **ISSCommandWithParameters**のサポートが公開されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML およびユーザー定義型 (UDT)。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**ICommandWithParameters**します。 継承した次の 3 つのメソッドだけでなく**ICommandWithParameters**;**GetParameterInfo**、 **MapParameterNames**、および**SetParameterInfo**;**ISSCommandWithParameters**サーバー固有のデータ型を処理するために使用される 2 つの新しいメソッドを提供します。  
  
> [!NOTE]  
>  **ISSCommandWithParameters**サービス コンポーネントが使用されますが、サービス コンポーネント自体はこのインターフェイスを使用していない場合は、インターフェイスを使用することができます。  
  
|方法|説明|  
|------------|-----------------|  
|[Isscommandwithparameters::getparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-getparameterproperties-ole-db.md)|1 つを返します**SSPARAMPROPS**配列内のコマンドに渡された各 UDT または XML パラメーターのプロパティ セット構造体が、他の種類のパラメーターの none が返されます。|  
|[Isscommandwithparameters::setparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-setparameterproperties-ole-db.md)|各パラメーターの序数でパラメーターのプロパティを設定または一括でパラメーター プロパティを設定の配列を指定することによって**SSPARAMPROPS**構造体。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [XML データ型の使用](../native-client/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)  
  
  
