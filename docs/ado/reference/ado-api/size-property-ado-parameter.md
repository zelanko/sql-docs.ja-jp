---
title: Size プロパティ (ADO パラメーター) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 643e5e4603b91eb66e57bf3519b31a647fb49d5d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="size-property-ado-parameter"></a>Size プロパティ (ADO パラメーター)
バイト数または文字で、最大サイズを示す、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**バイトまたはキャラクターの値の最大サイズを示す値、**パラメーター**オブジェクト。  
  
## <a name="remarks"></a>解説  
 使用して、**サイズ**プロパティに書き込まれた値の最大サイズを決定またはからの読み取りを[値](../../../ado/reference/ado-api/value-property-ado.md)のプロパティ、**パラメーター**オブジェクト。  
  
 可変長データ型を指定するかどうか、**パラメーター**オブジェクト (たとえば、**文字列**など、入力**それぞれ**)、オブジェクトを設定する必要があります**サイズ**プロパティに追加する前に、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションです。 それ以外の場合、エラーが発生します。  
  
 既に追加した場合、**パラメーター**オブジェクトを**パラメーター**のコレクション、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトとする型を可変長データ型に変更を行う必要があります設定、**パラメーター**オブジェクトの**サイズ**を実行する前に、プロパティ、**コマンド**オブジェクトです。 それ以外の場合、エラーが発生します。  
  
 使用する場合、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)プロバイダーからパラメーター情報を取得するメソッドが 1 つまたは複数の可変長データ型を返します**パラメーター**オブジェクト、ADO が基づくパラメーターのメモリを割り当てることがあります潜在的なサイズの最大の実行中にエラーが発生する可能性があります。 エラーを回避するのには明示的に設定する、**サイズ**コマンドを実行する前にこれらのパラメーター プロパティ。  
  
 **サイズ**読み取り/書き込みプロパティです。  
  
## <a name="applies-to"></a>適用対象  
 [Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Size プロパティ (ADO Stream)](../../../ado/reference/ado-api/size-property-ado-stream.md)
