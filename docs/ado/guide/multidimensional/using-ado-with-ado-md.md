---
title: ADO MD | での ADO の使用Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, using with ADO MD
ms.assetid: cfae435e-2ac3-4312-8c1e-9ca4a74cd875
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3c634ec056d42e97dcbea3422a0e19a33596d54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923146"
---
# <a name="using-ado-with-ado-md"></a>ADO MD と ADO の併用
ADO と ADO MD は関連がありますが、個別のオブジェクトモデルです。 ADO には、データソースに接続したり、コマンドを実行したり、表形式のデータとスキーマメタデータを表形式で取得したり、プロバイダーのエラー情報を表示したりするためのオブジェクトが用意されています。 ADO MD には、多次元データを取得し、多次元スキーマメタデータを表示するためのオブジェクトが用意されています。  
  
 .MDP を使用する場合は、アプリケーションで ADO、ADO MD、またはその両方を使用することを選択できます。 プロジェクト内で両方のライブラリを参照することにより、.MDP によって提供される機能に完全にアクセスできるようになります。  
  
 多くの場合、コンシューマーは多次元データセットのフラット化された表形式ビューを取得すると便利です。 これを行うには、ADO[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトを使用します。 ADO MD**セル**セットのソースとしてではなく、**レコードセット**の[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドの***source***パラメーターとして、[セル](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)セットのソースを指定します。  
  
 また、オブジェクトの階層としてではなく、表形式ビューでスキーマメタデータを表示すると便利な場合もあります。 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの ADO [OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドを使用すると、スキーマ情報を含む**レコードセット**をユーザーが開くことができます。 **OpenSchema**メソッドの***QueryType***パラメーターには、具体的には mdps に関連する複数の[schemaenum](../../../ado/reference/ado-api/schemaenum.md)値があります。 これらの値は次のとおりです。  
  
-   **adSchemaCubes**  
  
-   **adSchemaDimensions**  
  
-   **adSchemaHierarchies**  
  
-   **adSchemaLevels**  
  
-   **adschemameasame**  
  
-   **adSchemaMembers**  
  
 ADO MD のプロパティまたはメソッドで ADO 列挙値を使用するには、プロジェクトで ADO ライブラリと ADO MD ライブラリの両方を参照する必要があります。 たとえば、ADO MD [State](../../../ado/reference/ado-md-api/state-property-ado-md.md)プロパティで ADO **adstate**列挙値を使用できます。 ライブラリへの参照を設定する方法の詳細については、開発ツールのドキュメントを参照してください。  
  
 ADO のオブジェクトとメソッドの詳細については、「 [ADO API リファレンス](../../../ado/reference/ado-api/ado-api-reference.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ADO MD オブジェクトモデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (多次元) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [多次元スキーマとデータの概要](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [多次元データの操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
