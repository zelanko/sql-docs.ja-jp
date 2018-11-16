---
title: ストアド プロシージャの引数と空間インデックスのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- spatial indexes [SQL Server], stored procedures
ms.assetid: ee26082b-c0ed-40ff-b5ad-f5f6b00f0475
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ccd9e2be26c8d514e17a4aa03af422cd648fe426
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666601"
---
# <a name="spatial-index-stored-procedures---arguments-and-properties"></a>空間インデックス ストアド プロシージャの引数とプロパティ
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックでは、空間インデックス ストアド プロシージャの引数とプロパティについて説明します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
 特定の空間インデックス ストアド プロシージャの構文については、次のトピックを参照してください。  
  
-   [sp_help_spatial_geometry_index &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="arguments"></a>引数  
 [  **@tabname =**] **'***tabname $***'**  
 空間インデックスが指定されているテーブルの修飾名または非修飾名です。  
  
 引用符が必要なのは、修飾されたテーブルを指定する場合のみです。 データベース名を含む完全修飾名を指定する場合、データベース名は現在のデータベースの名前である必要があります。 *tabname $* は**nvarchar**(776) で、既定値はありません。  
  
 [  **@indexname =** ] **'***indexname***'**  
 指定されている空間インデックスの名前です。 *indexname*は**sysname**既定値はありません。  
  
 [  **@verboseoutput =** ] **'***verboseoutput***'**  
 返されるプロパティの名前と値の範囲です。  
  
 0 = 主要プロパティ。  
  
 \>0 = すべてのプロパティ  
  
 *verboseoutput*は**tinyint**既定値はありません。  
  
 [  **@query_sample =** ] **'***query_sample***'**  
 インデックスの有効性のテストに使用できる代表のクエリ サンプルです。 代表のオブジェクトまたはクエリ ウィンドウを指定できます。 *query_sample*は**geometry**既定値はありません。  
  
 [  **@xml_output =** ] **'***xml_output***'**  
 XML フラグメントで結果セットを返す出力パラメーターです。 *xml_output*は**xml**既定値はありません。  
  
## <a name="properties"></a>[プロパティ]  
 設定**@verboseoutput** = 0; 次の表に示すように、コア プロパティを返す**@verboseoutput** > 0 を空間インデックスのすべてのプロパティを返します。  
  
 **Base_Table_Rows**  
 ベース テーブル内の行数。 値は**bigint**します。  
  
 **Bounding_Box_xmin**  
 X の最小の境界ボックスのプロパティの空間インデックスの**geometry**型。 このプロパティの値は NULL です**geography**型。 値は**float**します。  
  
 **Bounding_Box_ymin**  
 境界ボックスのプロパティの空間インデックスの Y の最小値**geometry**型。 このプロパティの値は NULL です**geography**型。 値は**float**します。  
  
 **Bounding_Box_xmax**  
 境界ボックスのプロパティの空間インデックスの X の最大値**geometry**型。 このプロパティの値は NULL です**geography**型。 値は**float**します。  
  
 **Bounding_Box_ymax**  
 境界ボックスのプロパティの空間インデックスの Y の最大値**geometry**型。 このプロパティの値は NULL です**geography**型。 値は**float**します。  
  
 **Grid_Size_Level_1**  
 空間インデックスのレベル 1 グリッド密度です。  
  
 LOW の場合は 16。  
  
 MEDIUM の場合は 64。  
  
 HIGH の場合は 256。  
  
 値は**int**します。  
  
 **Grid_Size_Level_2**  
 空間インデックスのレベル 2 のグリッド密度です。  
  
 LOW の場合は 16。  
  
 MEDIUM の場合は 64。  
  
 HIGH の場合は 256。  
  
 値は**int**します。  
  
 **Grid_Size_Level_3**  
 空間インデックスのレベル 3 のグリッド密度です。  
  
 LOW の場合は 16。  
  
 MEDIUM の場合は 64。  
  
 HIGH の場合は 256。  
  
 値は**int**します。  
  
 **Grid_Size_Level_4**  
 空間インデックスのレベル 4 のグリッド密度。  
  
 LOW の場合は 16。  
  
 MEDIUM の場合は 64。  
  
 HIGH の場合は 256。  
  
 値は**int**します。  
  
 **Cells_Per_Object**  
 オブジェクトごとのセル数 (インデックス プロパティ)。 値は**int**します。  
  
 **Total_Primary_Index_Rows**  
 インデックス内の行数。 値は**bigint**します。  
  
 **Total_Primary_Index_Pages**  
 インデックス内のページ数。 値は**bigint**します。  
  
 **Average_Number_Of_Index_Rows_Per_Base_Row**  
 インデックスの行数/ベース テーブルの行数。 値は**bigint**します。  
  
 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**  
 代表のクエリ サンプルがの境界ボックス外にあるかどうかを示す、 **geometry**インデックスと、ルート セル (レベル 0 のセル)。 この値は、0 (レベル 0 のセル外) または 1 のいずれかです。 レベル 0 のセル内にある場合、調査対象のインデックスは、クエリ サンプルに適切なインデックスではありません。 これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_ObjectCells_In_Level0_In_Index**  
 レベル 0 でテセレーションされるインデックス付きオブジェクトのセル インスタンスの数 (ルート セルでは、境界ボックスの外**geometry**)。 これは主要プロパティです。 値は**bigint**します。  
  
 **Geometry**インデックスの場合、これが発生、インデックスの境界ボックスがデータ ドメインより小さい場合。 クエリ ウィンドウが境界外部分的になる場合、セカンダリ フィルターのボックスし、インデックスのパフォーマンスが低下レベル 0 のオブジェクトの多数があります (たとえば、 **Total_Number_Of_ObjectCells_In_Level0_For_QuerySample**は 1)。 クエリ ウィンドウが境界ボックス内にある場合は、レベル 0 のオブジェクトが多数あると、インデックスのパフォーマンスがむしろ向上することがあります。  
  
 NULL および空のインスタンスは、レベル 0 でカウントされますが、パフォーマンスには影響しません。 レベル 0 には、ベース テーブルの NULL および空のインスタンスと同じ数のセルが存在することになります。 **Geography**インデックス レベル 0 は NULL として数のセルと +1 に空のインスタンスのセルがあります、クエリ サンプルが 1 としてカウントされるためです。  
  
 **Total_Number_Of_ObjectCells_In_Level1_In_Index**  
 レベル 1 の精度でテセレーションされるインデックス付きオブジェクトのセル インスタンスの数。 これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_ObjectCells_In_Level2_In_Index**  
 レベル 2 の精度でテセレーションされるインデックス付きオブジェクトのセル インスタンスの数。 これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_ObjectCells_In_Level3_In_Index**  
 レベル 3 の精度でテセレーションされるインデックス付きオブジェクトのセル インスタンスの数。 これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_ObjectCells_In_Level4_In_Index**  
 レベル 4 の精度でテセレーションされるインデックス付きオブジェクトのセル インスタンスの数。 これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_interior_ObjectCells_In_Level1_In_Index**  
 テセレーション レベル 1 のオブジェクトで完全に覆われ、そのため、内部オブジェクトにはセルの数です。 (Cell_attributevalue は 2 です。)これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_interior_ObjectCells_In_Level2_In_Index**  
 テセレーション レベル 2 のオブジェクトで完全に覆われ、そのため、内部オブジェクトにはセルの数です。 (Cell_attribute 値は 2 です。)これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_interior_ObjectCells_In_Level3_In_Index**  
 テセレーションでオブジェクトによって完全に覆われるセルの数は、レベル 3 およびはそのため、内部オブジェクトにします。 (Cell_attribute 値は 2 です。)これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_interior_ObjectCells_In_Level4_In_Index**  
 テセレーション レベル 4 のオブジェクトで完全に覆われていることにより、そのオブジェクトの内側にあるセルの数  (Cell_attribute 値は 2 です。)これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level1_In_Index**  
 テセレーション レベル 1 のオブジェクトと交差するセルの数。 (Cell_attribute 値は 1 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level2_In_Index**  
 テセレーション レベル 2 のオブジェクトと交差するセルの数。 (Cell_attribute 値は 1 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level3_In_Index**  
 テセレーション レベル 3 にあるオブジェクトと交差するセルの数。 (Cell_attribute 値は 1 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_intersecting_ObjectCells_In_Level4_In_Index**  
 テセレーション レベル 4 のオブジェクトと交差するセルの数  (Cell_attribute 値は 1 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_For_QuerySample**  
 クエリ サンプルが境界ボックス外でルート セル 0 内にあり、境界ボックスに接しているかどうかを示します。 これは主要プロパティです。 値は**bigint**します。  
  
> [!NOTE]  
>  この情報は、境界ボックスに近接しているものの含まれなかったオブジェクトがあるかどうかを判断する場合にのみ役立ちます。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level0_In_Index**  
 境界ボックスに接しているレベル 0 のオブジェクト数  (Cell_attribute 値は 0 です)。値は**bigint**します。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level1_In_Index**  
 テセレーション レベル 1 グリッド セルの境界に接するオブジェクト セルの数。 (Cell_attribute 値は 0 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level2_In_Index**  
 テセレーション レベル 2 のグリッド セルの境界に接するオブジェクト セルの数。 (Cell_attribute 値は 0 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level3_In_Index**  
 テセレーション レベル 3 のグリッド セルの境界に接するオブジェクト セルの数。 (Cell_attribute 値は 0 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Total_Number_Of_Border_ObjectCells_In_Level4_In_Index**  
 テセレーション レベル 4 のグリッド セルの境界に接するオブジェクト セルの数  (Cell_attribute 値は 0 です)。これは主要プロパティです。 値は**bigint**します。  
  
 **Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 オブジェクトで覆われたリーフ セルを含むグリッドの合計領域 (リーフ セルの合計) の割合。  
  
 たとえば、合計で 100 のリーフ セルになる領域を覆う 4 つの異なるグリッド レベルの 10 のセルに、1 つのオブジェクトがテセレーションされます。 このオブジェクトによって完全に覆われる内部セルが 3 つあるとします。 この 3 つの内部セルで覆われる領域は、42 のリーフ セルに相当します。 この場合、覆われている領域の割合は 42% です。 これにより、インデックス内のオブジェクトがどの程度細分化されているかを適切に測定できます。  
  
 値は**float**します。  
  
 **Intersecting_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 同じ**Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**こと部分的にカバーされたセルを除いて、します。 値は**float**します。  
  
 **Border_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**  
 同じ**Interior_To_Total_Cells_Normalized_To_Leaf_Grid_Percentage**こと境界のセルを除いて。 値は**float**します。  
  
 **Average_Cells_Per_Object_Normalized_To_Leaf_Grid**  
 リーフ グリッドに正規化されたオブジェクトごとの平均セル数。 これにより、オブジェクトの空間サイズ、つまりオブジェクトの大きさがわかります。 値は**float**します。  
  
 **Average_Objects_PerLeaf_GridCell**  
 インデックスのスパースの度合い。 リーフ セルごとのオブジェクトの平均数です。 値は**float**します。  
  
 **Number_Of_SRIDs_Found**  
 インデックスおよび列内の一意な SRID の数。 値は**int**します。  
  
 列には複数の SRID を含めることができ、異なる SRID のオブジェクトは交差しないので、SRID の数はインデックスの選択度を表します。  
  
 **Width_Of_Cell_In_Level1**  
 インデックス作成グリッド内のセルの幅。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Width_Of_Cell_In_Level2**  
 インデックス作成グリッド内のセルの幅。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Width_Of_Cell_In_Level3**  
 インデックス作成グリッド内のセルの幅。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Width_Of_Cell_In_Level4**  
 インデックス作成グリッド内のセルの幅。 測定単位はインデックスで指定され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Height_Of_Cell_In_Level1**  
 インデックス作成グリッド内のセルの高さ。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Height_Of_Cell_In_Level2**  
 インデックス作成グリッド内のセルの高さ。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Height_Of_Cell_In_Level3**  
 インデックス作成グリッド内のセルの高さ。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Height_Of_Cell_In_Level4**  
 インデックス作成グリッド内のセルの高さ。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Area_Of_Cell_In_Level1**  
 インデックス作成グリッド内のセルの領域。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Area_Of_Cell_In_Level2**  
 インデックス作成グリッド内のセルの領域。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Area_Of_Cell_In_Level3**  
 インデックス作成グリッド内のセルの領域。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **Area_Of_Cell_In_Level4**  
 インデックス作成グリッド内のセルの領域。 測定単位は、インデックスによって提供され、インデックス付きデータの SRID によって異なります。 値は**float**します。  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level1**  
 レベル 1 のセルによる境界ボックスのカバレッジの割合。 値は**float**します。  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level2**  
 レベル 2 のセルによる境界ボックスのカバレッジの割合。 値は**float**します。  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level3**  
 レベル 3 のセルによる境界ボックスのカバレッジの割合。 値は**float**します。  
  
 **CellArea_To_BoundingBoxArea_Percentage_In_Level4**  
 レベル 4 のセルによる境界ボックスの使用割合。 値は**float**します。  
  
 **Number_Of_Rows_Selected_By_Primary_Filter**  
 プライマリ フィルターによって選択された行数。 これは主要プロパティです。 値は**bigint です。**  
  
 **Number_Of_Rows_Selected_By_Internal_Filter**  
 内部フィルターによって選択された行数。 これらの行では、セカンダリ フィルターは呼び出されません。 これは主要プロパティです。 値は**bigint です。**  
  
 返される数はのみに適用されます**STintersects**します。  
  
 **Number_Of_Times_Secondary_Filter_Is_Called**  
 セカンダリ フィルターの呼び出し回数。 これは主要プロパティです。 値は**bigint です。**  
  
 **Percentage_Of_Rows_NotSelected_By_Primary_Filter**  
 ベース テーブル内に N 行あり、P 行がプライマリ フィルターによって選択されたとすると、割合として (N-P)/N を返します。 これは主要プロパティです。 値は**浮動小数点数。**  
  
 **Percentage_Of_Primary_Filter_Rows_Selected_By_internal_Filter**  
 P 行がプライマリ フィルターによって選択され、S 行が内部フィルターによって選択されたとすると、割合として S/P を返します。 この割合が大きくなると、インデックスで、パフォーマンス コストが高いセカンダリ フィルターを使用せずに済むようになります。 これは主要プロパティです。 値は**浮動小数点数。**  
  
 **Number_Of_Rows_Output**  
 クエリで出力された行数。 これは主要プロパティです。 値は**bigint です。**  
  
 **Internal_Filter_Efficiency**  
 O が出力された行数だとすると、割合として S/O を返します。 これは主要プロパティです。 値は**浮動小数点数。**  
  
 **Primary_Filter_Efficiency**  
 P 行がプライマリ フィルターと O で選択されている場合は、出力行の数に対する割合としてこの returnsO P/です。 プライマリ フィルターの効率が高くなると、セカンダリ フィルターで処理する必要がある偽陽性が少なくなります。 これは主要プロパティです。 値は**浮動小数点数。**  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーのメンバーである必要があります、**パブリック**ロール。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。 これは、すべての空間インデックス ストアド プロシージャに当てはまります。  
  
## <a name="remarks"></a>コメント  
 NULL 値を含むプロパティは、返されるセットに含まれません。  
  
## <a name="examples"></a>使用例  
 例については、次のトピックを参照してください。  
  
-   [sp_help_spatial_geometry_index &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)  
  
-   [sp_help_spatial_geometry_index_xml &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)  
  
-   [sp_help_spatial_geography_index &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)  
  
-   [sp_help_spatial_geography_index_xml &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-xml-transact-sql.md)  
  
## <a name="requirements"></a>要件  
  
## <a name="see-also"></a>参照  
 [空間インデックス ストアド プロシージャ&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [XQuery の基礎](../../xquery/xquery-basics.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
