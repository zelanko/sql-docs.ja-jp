---
title: 介在する COMPUTE コマンドを使用してコマンドをパラメーター化された |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b33feb8075babd50f67b6c01da5afadcd1c33e0b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700521"
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>介在する COMPUTE コマンドを含むパラメーター化されたコマンド
一般的なパラメーター化された shape の APPEND コマンドが親を作成する句を**レコード セット**クエリ コマンドと子を作成するもう 1 つの句**Recordset**でパラメーター化クエリ コマンド -パラメーターのプレース ホルダーを含むコマンドは、(、疑問符"?")。 シェイプ**レコード セット**親が上位のレベルを占有する 2 つのレベルがあり、子は、下位のレベルを占有します。  
  
 子を作成する句**Recordset**が現在任意の数の図形を入れ子になったコンピューティング コマンドでは、最も深く入れ子になったコマンドにパラメーター化クエリが含まれています。 シェイプ**レコード セット**親が最上位のレベルを占有する、複数のレベルには、低位側のレベルと任意の数の子が占有**レコード セット**s によって生成された、コンピューティングの図形のコマンドは、介在するレベルを占有します。  
  
 介在するを作成するためのコマンドは、この機能を shapeCOMPUTE の能力をグループ化および集計関数を呼び出す一般的な使用**Recordset**子に関する分析情報を持つオブジェクト**レコード セット**. さらに、これはパラメーター化された図形コマンドであるため、毎回、親のチャプター列は、新しい子**Recordset**を取得できます。 間のレベルは、子から派生した、ため、これらも再計算されます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
