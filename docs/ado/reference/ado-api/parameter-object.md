---
title: "パラメーター オブジェクト |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec8556b03b2f0d3a3d7d439ae223385860040c63
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="parameter-object"></a>Parameter オブジェクト
パラメーターまたはに関連付けられている引数を表します、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトがパラメーター化されたクエリまたはストアド プロシージャに基づいています。  
  
## <a name="remarks"></a>解説  
 プロバイダーの多くは、パラメーター化コマンドをサポートします。 これらは、目的のアクションが定義されている、1 回のコマンドが、変数 (またはパラメーター) は、コマンドのいくつかの詳細を変更するために使用します。 たとえば、SQL SELECT ステートメントでは、WHERE 句、および並べ替え句の列名を定義するのに別の一致条件を定義するのにパラメーターを使用する可能性があります。  
  
 **パラメーター**オブジェクトは、パラメーター化クエリに関連付けられているパラメーターを表すか、ストアド プロシージャの入力/出力引数および戻り値。 プロバイダー、いくつかのコレクション、メソッド、またはのプロパティの機能によって、**パラメーター**オブジェクトを使用できない可能性があります。  
  
 コレクション、メソッド、およびプロパティの使用、**パラメーター**オブジェクトを次を行うことができます。  
  
-   設定または使用して、パラメーターの名前を返す、[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティです。  
  
-   設定または使用して、パラメーターの値を返す、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティです。 **値**の既定のプロパティは、**パラメーター**オブジェクト。  
  
-   設定またはパラメーターの特性を返す、[属性](../../../ado/reference/ado-api/attributes-property-ado.md)、[方向](../../../ado/reference/ado-api/direction-property.md)、[精度](../../../ado/reference/ado-api/precision-property-ado.md)、 [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)、 [サイズ](../../../ado/reference/ado-api/size-property-ado-parameter.md)、および[型](../../../ado/reference/ado-api/type-property-ado.md)プロパティです。  
  
-   Long バイナリまたは文字データを持つパラメーターを渡す、 [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)メソッドです。  
  
-   プロバイダー固有の属性を使用して、アクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 名前がわかっていて、パラメーターのプロパティに関連付けられているが、呼び出すストアド プロシージャまたはパラメーター化クエリを使用することができます、 [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)メソッドを作成**パラメーター**オブジェクト適切なプロパティの設定および使用すると、 [Append](../../../ado/reference/ado-api/append-method-ado.md)に追加する方法、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。 これにより設定を呼び出さずにパラメーター値を返す、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを**パラメーター**プロバイダーからパラメーター情報を取得するコレクション、可能性がありますリソースを消費する操作です。  
  
 **パラメーター**オブジェクトはスクリプトを実行しても安全ではありません。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [パラメーター オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
