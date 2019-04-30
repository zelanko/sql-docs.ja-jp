---
title: Direction プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Direction
helpviewer_keywords:
- Direction property
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df2f7cc5eadce7d4f8f61674f4915ec3b1561e02
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180962"
---
# <a name="direction-property"></a>Direction プロパティ
示すかどうか、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)入力パラメーター、出力パラメーター、入力パラメーターと、出力パラメーターを表すパラメーターがストアド プロシージャからの戻り値の場合、または。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を[値](../../../ado/reference/ado-api/parameterdirectionenum.md)値。  
  
## <a name="remarks"></a>コメント  
 使用して、**方向**プロパティに、またはプロシージャからパラメーターを渡す方法を指定します。 **方向**読み取り/書き込みプロパティです。 これにより、この情報を返さないプロバイダーと連携するか、ADO プロバイダーに、パラメーター情報を取得するの余分な呼び出しを行う必要がない場合は、この情報を設定します。  
  
 一部のプロバイダーは、ストアド プロシージャのパラメーターの方向を判断できます。 このような場合は、設定する必要があります、**方向**プロパティ クエリを実行する前にします。  
  
## <a name="applies-to"></a>適用対象  
 [Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
