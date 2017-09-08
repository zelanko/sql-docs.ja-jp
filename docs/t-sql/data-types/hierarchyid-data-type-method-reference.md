---
title: "hierarchyid (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- hierarchyid
- hierarchyid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Hierarchy data type
- hierarchyid data type
ms.assetid: 69b756e0-a1df-45b3-8a24-6ded8658aefe
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44299e7ddb90bdd52e2638dd859993513bd6f966
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyid-data-type-method-reference"></a>hierarchyid データ型メソッド リファレンス
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**Hierarchyid**データ型は可変長の場合は、システム データ型します。 使用して**hierarchyid**を階層内の位置を表します。 **hierarchyid** 型の列が自動的にツリーを表すことはありません。 行と行の間に必要なリレーションシップが反映されるよう、 **hierarchyid** 値を生成して割り当てるのは、アプリケーションの役割です。
  
値、 **hierarchyid** データ型は、ツリー階層内の位置を表します。 値を **hierarchyid** 、次のプロパティがあります。
  
-   非常にコンパクト  
     平均を持つツリー内のノードを表すために必要なビット数 *n* ノードは平均ファンアウト (ノードの子の平均数) によって異なります。 小さなファンアウト場合 (0 ~ 7)、このサイズは約 6\*logA *n* ビット、A は平均ファンアウトします。 平均ファンアウトが 6 レベルで、100,000 人から成る組織階層の場合、1 つのノードには約 38 ビットが必要です。 格納時には、これが 40 ビット (5 バイト) に切り上げられます。  
-   深さ優先順で比較  
     **a** と **b** の 2 つの **hierarchyid** 値がある場合、**a<b** は、ツリーの深さ優先検査において a が b の前に来ることを意味します。 インデックス **hierarchyid** に深さ優先順では、データ型があり、深さ優先検査で近接ノードは互いに近い格納します。 たとえば、あるレコードの子は、そのレコードに隣接して格納されます。 詳細については、次を参照してください。[階層データ & #40 です。SQL Server &#41;](../../relational-databases/hierarchical-data-sql-server.md).  
-   任意の挿入および削除のサポート  
     [GetDescendant](../../t-sql/data-types/getdescendant-database-engine.md) メソッドを使用すると、指定したノードの右側や左側、または任意の 2 つの兄弟間に、いつでも兄弟を生成できます。 階層に対して任意の数のノードを挿入または削除しても、比較の特性は維持されます。 ほとんどの挿入や削除では、コンパクトさも維持されます。 ただし、2 ノード間に挿入した場合は、hierarchyid 値のコンパクトさがやや失われます。  
-   使用するエンコーディング、 **hierarchyid**型は 892 バイトに制限されています。 その結果、892 バイトに収まるように表現が多すぎますのレベルを持つノードで表せない、 **hierarchyid**型です。  
  
**Hierarchyid**型として CLR クライアントで使用できる、 **SqlHierarchyId**データ型。
  
## <a name="remarks"></a>解説  
**Hierarchyid**型が、ツリーのルートからノードへのパスをエンコードすることによって階層ツリー内の 1 つのノードに関する情報を論理的にエンコードします。 このようなパスは、ルートの後にアクセスされたすべての子の一連のノード ラベルとして論理的に表されます。 この表現はスラッシュによって開始されます。ルートのみを表すパスは、単一スラッシュで表されます。 ルートの下のレベルの各ラベルは、ドットで区切られた一連の整数としてエンコードされます。 子と子の比較は、ドットで区切られた一連の整数を辞書順で比較することにより行われます。 各レベルの後ろには、スラッシュが続きます。 したがって、スラッシュは親と子を区切ります。 たとえば、次に有効な**hierarchyid**パスの長さは 1、2、2、3、および 3 それぞれのレベルします。
  
-   /  
  
-   /1/  
  
-   /0.3.-7/  
  
-   /1/3/  
  
-   /0.1/0.2/  
  
ノードは、任意の位置に挿入できます。 ノードが後に挿入**/1/2**前に**/1/3/**として表すことが**/1/2.5**です。 0 の前に挿入されたノードの論理表現は、負の値となります。 たとえば前、に来るノード**/1/1/**として表すことが**/1/1/**です。 ノードに先頭のゼロを付けることはできません。 たとえば、 **/1 1.1/**が有効でが**/1/1.01**が無効です。 エラーを防ぐためには、ノードの挿入を使用して、 [GetDescendant](../../t-sql/data-types/getdescendant-database-engine.md)メソッドです。
  
## <a name="data-type-conversion"></a>データ型の変換
**Hierarchyid**データ型を次のように他のデータ型に変換できます。
-   使用して、 [ToString()](../../t-sql/data-types/tostring-database-engine.md)に変換する方法、 **hierarchyid**値として論理表現に、 **nvarchar (4000)**データ型。  
-   使用して[() を読み取る](../../t-sql/data-types/read-database-engine.md)と[Write ()](../../t-sql/data-types/write-database-engine.md)に変換する**hierarchyid**に**varbinary**です。  
-   転送する**hierarchyid** SOAP を使用したパラメーター最初を文字列としてキャストします。  
  
## <a name="upgrading-databases"></a>データベースのアップグレード
データベースをアップグレードするとき[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、新しいアセンブリおよび**hierarchyid**データ型は自動的にインストールされます。 アップグレード アドバイザーのルールにより、競合する名前を持つユーザー型またはアセンブリが検出されます。 アップグレード アドバイザーは、次のいずれかの方法によって、競合するアセンブリの名前の変更を推奨します。2 つの方法とは、競合する型の名前を変更するか、または 2 つの部分から構成される名前をコード内で使用して既存のユーザー型を参照するかのどちらかです。
  
データベースのアップグレード時に競合する名前を持つユーザー アセンブリが検出されると、このアセンブリの名前が自動的に変更され、データベースが問題のあるモードになります。
  
アップグレード時に競合する名前を持つユーザー型が検出された場合、特別な処理は実行されません。 アップグレード後は、古いユーザー型と新しいシステム型の両方が存在することになります。 ユーザー型は、2 つの部分から構成される名前を介してのみ使用できます。
  
## <a name="using-hierarchyid-columns-in-replicated-tables"></a>レプリケートされたテーブルでの hierarchyid 列の使用
型の列**hierarchyid**任意のレプリケートされたテーブルで使用できます。 アプリケーションの要件は、レプリケーション方法や (単方向または双方向)、使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって異なります。
  
### <a name="one-directional-replication"></a>一方向のレプリケーション
単方向レプリケーションには、サブスクライバー側で変更が行われないスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションが含まれます。 どの**hierachyid**使用して単方向レプリケーションは、のバージョンによって異なります。 1 つの列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サブスクライバーが実行されています。
-   A[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]パブリッシャーにレプリケートできる**hierachyid**列を[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]サブスクライバーには特別な注意事項です。  
-   A[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]パブリッシャーに変換する必要があります**hierarchyid**これらを実行しているサブスクライバーにレプリケートする列[!INCLUDE[ssEW](../../includes/ssew-md.md)]または以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssEW](../../includes/ssew-md.md)]以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サポートしていない**hierarchyid**列です。 このどちらかのバージョンを使用している場合でも、サブスクライバーにデータをレプリケートすることは可能です。 そのためには、互換性のあるデータ型に列を変換できるように、スキーマ オプションまたはパブリケーションの互換性レベル (マージ レプリケーションの場合) を設定する必要があります。  
  
どちらのシナリオでも、列のフィルター選択はサポートされています。 これは、フィルターで除外が含まれています。 **hierarchyid**列です。 行フィルターはサポートされて、フィルターではない限り、 **hierarchyid**列です。
  
### <a name="bi-directional-replication"></a>双方向のレプリケーション
双方向レプリケーションには、サブスクライバー側で変更が行われる、更新サブスクリプションを使用したトランザクション レプリケーション、ピア ツー ピア トランザクション レプリケーション、およびマージ レプリケーションが含まれます。 レプリケーションを持つテーブルを構成できます。 **hierarchyid**双方向のレプリケーションの列です。 次の要件と考慮事項に注意してください。
-   パブリッシャーおよびすべてのサブスクライバーで [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を実行している必要があります。  
-   レプリケーションでは、データはバイトとしてレプリケートされます。階層の整合性を保証するための検証は行われません。  
-   レプリケート元 (サブスクライバーまたはパブリッシャー) で変更が加えられた階層は、レプリケート先にレプリケートするときに維持されません。  
-   ハッシュ値**hierarchyid**列は生成されたデータベースに固有です。 したがって、パブリッシャー側とサブスクライバー側とで同じ値が生成され、異なる行に適用される可能性があります。 レプリケーションがこの条件のチェックされず、パーティションに組み込みの方法はありません**hierarchyid**の列の値を ID 列があるためです。 アプリケーションでは、このような検出されない競合を避けるために、制約またはその他のメカニズムを使用する必要があります。  
-   サブスクライバー側で挿入された行が孤立する場合があります。 挿入された行の親の行がパブリッシャー側で削除されている可能性があります。 その結果、サブスクライバーの行がパブリッシャー側で挿入されたときに検出されない競合が発生します。  
-   列フィルターが null 非許容を排除できない**hierarchyid**列: の既定値がないため、サブスクライバーからの挿入は失敗、 **hierarchyid**パブリッシャーの列です。  
-   行フィルターはサポートされて、フィルターではない限り、 **hierarchyid**列です。  
  
## <a name="see-also"></a>参照
[階層データ (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid データ型メソッド リファレンス](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

