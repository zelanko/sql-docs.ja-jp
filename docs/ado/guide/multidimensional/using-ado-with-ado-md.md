---
title: "ADO MD と ADO の併用 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 38df55c27ced6e0a7b32c321e2b3968bedb73aa1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-ado-with-ado-md"></a>ADO MD と ADO の併用
ADO および ADO MD は、関連するけれども、異なるオブジェクト モデルです。 ADO では、データ ソースへの接続、コマンドを実行する、表形式のデータとスキーマのメタデータを表形式での取得、およびプロバイダーのエラー情報を表示するためのオブジェクトを提供します。 ADO MD では、多次元データを取得し、マルチ ディメンション スキーマのメタデータを表示するためのオブジェクトを提供します。  
  
 MDP を操作するときに、ADO、ADO MD で、またはそのアプリケーションを使用して両方を使用できます。 両方のプロジェクト内のライブラリを参照する、MDP によって提供される機能に対するフル アクセス権をようなります。  
  
 多次元データセットのフラット化された、表形式のビューを取得する消費者の多くの場合に便利です。 ADO を使用してこれを行う[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 ソースを指定、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)として、***ソース***のパラメーター、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)のメソッド、 **Recordset**のソースとしてではなくADO MD**セルセット**です。  
  
 オブジェクトの階層ではなく、表形式ビューのスキーマのメタデータを表示すると役立つ場合もあります。 ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドを[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトが、ユーザーが開くことができます、 **Recordset**スキーマ情報を格納します。 ***QueryType***のパラメーター、 **OpenSchema**メソッドにはいくつか[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) MDPs に特に関連する値。 これらの値は次のとおりです。  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adSchemaMeasures**  
  
-   **adSchemaMembers**  
  
 ADO MD プロパティまたはメソッドでは、ADO 列挙の値を使用するに、プロジェクトは、ADO および ADO MD の両方のライブラリを参照する必要があります。 たとえば、ADO を使用することができます**adState** ADO md の列挙値[状態](../../../ado/reference/ado-md-api/state-property-ado-md.md)プロパティです。 ライブラリへの参照を確立する方法の詳細については、開発ツールのドキュメントを参照してください。  
  
 ADO オブジェクトやメソッドの詳細については、次を参照してください。、 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [ADO MD オブジェクト モデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (多次元) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [マルチ ディメンション スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [多次元データの操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)

