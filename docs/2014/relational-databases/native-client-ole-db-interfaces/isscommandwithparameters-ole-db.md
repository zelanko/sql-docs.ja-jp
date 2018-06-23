---
title: ISSCommandWithParameters (OLE DB) |Microsoft ドキュメント
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
api_name:
- ISSCommandWithParameters (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 90359b753baff55d70c00727b8230c41059ceaa3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085868"
---
# <a name="isscommandwithparameters-ole-db"></a>ISSCommandWithParameters (OLE DB)
  **ISSCommandWithParameters**のサポートが公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML、およびユーザー定義型 (UDT)。 これは、主要な OLE DB インターフェイスから継承される省略可能なインターフェイス**ICommandWithParameters**です。 継承される 3 つのメソッドだけでなく**ICommandWithParameters**です。**GetParameterInfo**、 **MapParameterNames**、および**SetParameterInfo**です。**ISSCommandWithParameters**サーバー固有のデータ型を処理するために使用する 2 つの新しいメソッドを提供します。  
  
> [!NOTE]  
>  **ISSCommandWithParameters**サービス コンポーネントを使用すると、サービス コンポーネント自体がこのインターフェイスを使用していない場合は、インターフェイスを使用することができます。  
  
|方法|説明|  
|------------|-----------------|  
|[Isscommandwithparameters::getparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-getparameterproperties-ole-db.md)|1 つを返します**SSPARAMPROPS**プロパティ セット構造体には、コマンドに渡された各 UDT または XML パラメーターの配列が、他の種類のパラメーターに対して none が返されます。|  
|[Isscommandwithparameters::setparameterproperties &#40;OLE DB&#41;](isscommandwithparameters-setparameterproperties-ole-db.md)|序数の順に各パラメーターをパラメーターのプロパティを設定またはの配列を指定して一括でパラメーター プロパティを設定**SSPARAMPROPS**構造体。|  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [XML データ型の使用](../native-client/features/using-xml-data-types.md)   
 [ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)  
  
  