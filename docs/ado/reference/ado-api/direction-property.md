---
description: Direction プロパティ
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 37987e58829b1b6957b4fe1de440aaeb4aae1763
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444054"
---
# <a name="direction-property"></a>Direction プロパティ
[パラメーター](../../../ado/reference/ado-api/parameter-object.md)が入力パラメーター、出力パラメーター、入力パラメーター、および出力パラメーターを表すか、またはパラメーターがストアドプロシージャからの戻り値であるかを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 [Parameterdirection 列挙](../../../ado/reference/ado-api/parameterdirectionenum.md)値を設定または返します。  
  
## <a name="remarks"></a>解説  
 **Direction**プロパティを使用して、プロシージャとの間でパラメーターがどのように渡されるかを指定します。 **Direction**プロパティは読み取り/書き込み可能です。これにより、この情報を返さないプロバイダーを使用したり、パラメーター情報を取得するために ADO によってプロバイダーの呼び出しを追加する必要がない場合に、この情報を設定したりできます。  
  
 プロバイダーによっては、ストアドプロシージャ内のパラメーターの方向を特定できないことがあります。 このような場合は、クエリを実行する前に **Direction** プロパティを設定する必要があります。  
  
## <a name="applies-to"></a>適用対象  
 [Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、Size、Direction プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
