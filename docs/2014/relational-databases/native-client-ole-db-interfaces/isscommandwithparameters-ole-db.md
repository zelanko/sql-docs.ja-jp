---
title: ISSCommandWithParameters (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c55af9d21c669bd452de2bac9db56d158febc449
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704802"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
  **Isscommandwithparameters**は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、XML およびユーザー定義型 (UDT) のサポートを公開します。 これは、コア OLE DB インターフェイス**ICommandWithParameters**から継承する省略可能なインターフェイスです。 **ICommandWithParameters**から継承された3つのメソッドに加えて、**Getparameterinfo**、 **Mapparameternames**、および**setparameterinfo**;**Isscommandwithparameters**には、サーバー固有のデータ型を処理するために使用される2つの新しいメソッドが用意されています。  
  
> [!NOTE]  
>  **Isscommandwithparameters**インターフェイスは、サービスコンポーネントが使用されている場合に使用できますが、サービスコンポーネント自体はこのインターフェイスを使用しません。  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](isscommandwithparameters-getparameterproperties-ole-db.md)|コマンドに渡された各 UDT パラメーターまたは XML パラメーターごとに、1 つの **SSPARAMPROPS** プロパティ セット構造体を返します。他の型のパラメーターの場合、戻り値はありません。|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](isscommandwithparameters-setparameterproperties-ole-db.md)|序数に基づいてパラメーターごとにパラメーターのプロパティを設定するか、または**Ssparc Amprops**構造体の配列を指定して一括パラメータープロパティを設定します。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [XML データ型の使用](../native-client/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)  
  
  
