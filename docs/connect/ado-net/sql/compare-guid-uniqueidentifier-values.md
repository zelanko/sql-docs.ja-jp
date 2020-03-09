---
title: GUID と uniqueidentifier 値の比較
description: SQL Server と .NET で GUID および uniqueidentifier 値を操作する方法を示します。
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 22d27f9a80765aacdfab25c568e8e2635f1779cc
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2020
ms.locfileid: "78897020"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>GUID と uniqueidentifier 値の比較

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server のグローバル一意識別子 (GUID) データ型は、16 バイトのバイナリ値を格納する `uniqueidentifier` データ型によって表されます。 GUID はバイナリ数値であり、多くのサイトの多くのコンピューターがあるネットワーク内で一意にする必要がある識別子として主に使用されます。 GUID は、Transact-SQL NEWID 関数を呼び出して生成でき、全世界で一意であることが保証されます。 詳細については、「[uniqueidentifier (Transact-SQL)](../../../t-sql/data-types/uniqueidentifier-transact-sql.md)」を参照してください。  
  
## <a name="working-with-sqlguid-values"></a>SqlGuid 値の操作  
GUID 値は長く不明瞭なため、ユーザーにとって意味がありません。 キー値にランダムに生成された GUID を使用しており、大量の行を挿入した場合、インデックスにランダムな I/O が取り込まれるため、パフォーマンスが低下する可能性があります。 GUID はさらに、他のデータ型と比較すると比較的大きいものになります。 一般に、他のデータ型が適していないきわめて限られたシナリオでのみ、GUID を使用することが推奨されます。  
  
### <a name="comparing-guid-values"></a>GUID 値の比較  
`uniqueidentifier` 型の値には比較演算子が使用できます。 しかし、2 つの値のビット パターンを比較することによって、順序付けは実装されません。 `uniqueidentifier` 値に対して実行可能な唯一の操作は、比較 (=、<>、\<、>、\<=、>=) と NULL の確認 (IS NULL および IS NOT NULL) です。 他の算術演算子は使用できません。  
  
<xref:System.Guid> と <xref:System.Data.SqlTypes.SqlGuid> はどちらにも、異なる GUID 値を比較するための `CompareTo` メソッドがあります。 ただし、`System.Guid.CompareTo` と `SqlTypes.SqlGuid.CompareTo` の実装方法は異なります。 <xref:System.Data.SqlTypes.SqlGuid> は SQL Server の動作を使用して `CompareTo` を実装し、値の最後の 6 バイトが最も重要になります。 <xref:System.Guid> は 16 バイトすべてを評価します。 次の例は、この動作の違いを示しています。 コードの最初のセクションは、並べ替えられていない <xref:System.Guid> 値を示しており、コードの 2 番目のセクションは並べ替えられた <xref:System.Guid> 値を示しています。 3 番目のセクションは、並べ替えられた <xref:System.Data.SqlTypes.SqlGuid> 値を示しています。 コード リストの下に出力を示しています。  
  
[!code-csharp[DataWorks SqlGuid#1](~/../sqlclient/doc/samples/SqlGuid.cs#1)]
  
この例の結果は、次のようになります。  
  
```console
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server のデータ型と ADO.NET](sql-server-data-types.md)
