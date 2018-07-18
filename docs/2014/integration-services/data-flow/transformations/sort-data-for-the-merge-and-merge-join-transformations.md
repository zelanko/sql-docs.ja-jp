---
title: マージ変換およびマージ結合変換用にデータを並べ替える | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 21b60f8b5007ae574ab48bdd46e2e8f430b299cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316062"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>マージ変換およびマージ結合変換用にデータを並べ替える
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]のマージ変換およびマージ結合変換では、入力データが並べ替えられている必要があります。 入力データは物理的に並べ替える必要があります。さらに、変換元の出力および出力列、または上流の変換の出力および出力列に対して、並べ替えオプションを設定する必要があります。 並べ替えオプションでデータの並べ替えを設定していても、実際にデータの並べ替えが行われない場合、マージ操作やマージ結合操作で予測できない結果が発生します。  
  
## <a name="sorting-the-data"></a>データを並べ替える  
 データを並べ替えるには、次のいずれかの方法を使用します。  
  
-   変換元で、データの読み込みに使用されるステートメントで ORDER BY 句を使用します。  
  
-   データ フローで、マージ変換またはマージ結合変換の前に並べ替え変換を挿入します。  
  
 データが文字列データの場合、マージ変換およびマージ結合変換では、文字列値が Windows 照合順序を使用して並べ替えられている必要があります。 Windows 照合順序を使用して並べ替えた文字列値を、マージ変換およびマージ結合変換に指定するには、次の手順を実行します。  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>Windows 照合順序を使用して並べ替えた文字列値を指定するには  
  
-   並べ替え変換を使用して、データを並べ替えます。  
  
     並べ替え変換では Windows 照合順序を使用して文字列値を並べ替えます。  
  
     — または —  
  
-   Transact-SQL の CAST 演算子を使用して最初に `varchar` 値を `nvarchar` 値にキャストし、次に Transact-SQL ORDER BY 句を使用してデータを並べ替えます。  
  
    > [!IMPORTANT]  
    >  ORDER BY 句では文字列値の並べ替えに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 照合順序を使用するため、ORDER BY 句のみを使用することはできません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 照合順序を使用すると、Windows 照合順序とは異なる並べ替え順序になる場合があります。この場合、マージ変換またはマージ結合変換で予期しない結果になることがあります。  
  
## <a name="setting-sort-options-on-the-data"></a>データに対する並べ替えオプションの設定  
 マージ変換およびマージ結合変換にデータを提供する変換元または上流の変換に対して、設定する必要のある重要な並べ替えプロパティが 2 つあります。  
  
-   データが並べ替えられているかどうかを示す、出力の `IsSorted` プロパティ。 このプロパティに設定する必要があります`True`します。  
  
    > [!IMPORTANT]  
    >  値を設定、`IsSorted`プロパティを`True`もデータは並べ替えられません。 このプロパティでは、データが既に並べ替えられている下流コンポーネントにヒントのみを提供します。  
  
-   `SortKeyPosition`列を並べ替えるかどうか、列の並べ替え順序、および複数の列が並べ替えられる順序を示す出力列のプロパティ。 このプロパティは、並べ替えられるデータの各列に対して設定する必要があります。  
  
 並べ替え変換を使用してデータを並べ替える場合、並べ替え変換によって、これらの両方のプロパティが、マージ変換またはマージ結合変換の必要に応じて設定されます。 並べ替え変換の設定は、`IsSorted`その出力のプロパティ`True`、設定と、`SortKeyPosition`その出力列のプロパティ。  
  
 ただし、データの並べ替えに並べ替え変換を使用しない場合は、変換元または上流の変換でこれらの並べ替えプロパティを手動で設定する必要があります。 変換元または上流の変換で並べ替えプロパティを手動で設定するには、次の手順を実行します。  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>変換元コンポーネントまたは変換コンポーネントの並べ替え属性を手動で設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブで、適切な変換元または上流の変換を見つけるか、 **[ツールボックス]** からデザイン画面に、変換元または上流の変換をドラッグします。  
  
4.  コンポーネントを右クリックし、 **[詳細エディターの表示]** をクリックします。  
  
5.  **[入力プロパティと出力プロパティ]** タブをクリックします。  
  
6.  クリックして**\<コンポーネント名 > 出力**、設定、`IsSorted`プロパティを`True`します。  
  
    > [!NOTE]  
    >  手動で設定した場合、`IsSorted`プロパティへの出力の`True`データが並べ替えられていないとがありますに欠落データまたは下流の結合またはマージ結合変換の変換で不良データの比較、パッケージを実行するときにします。  
  
7.  **[出力列]** を展開します。  
  
8.  指定する列が並べ替えられ、設定をクリックしてその`SortKeyPosition`プロパティを次のガイドラインに従って、0 以外の整数値に。  
  
    -   整数値は、1 から始まって 1 ずつ増加する連続した数字を表す必要があります。  
  
    -   正の整数値は、昇順の並べ替え順序を示します。  
  
    -   負の整数値は、降順の並べ替え順序を示します (負の数値が設定されると、その数値の絶対値によって、並べ替え順での列の位置が決まります)。  
  
    -   既定値は 0 で、その列が並べ替えられないことを示します。 並べ替えに加えない出力列では、値を 0 のままにします。  
  
     `SortKeyPosition` プロパティの設定方法の例として、データを変換元に読み込む、次の Transact-SQL ステートメントについて考えてみます。  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     このステートメントでは、設定、`SortKeyPosition`次のように各列のプロパティ。  
  
    -   ColumnA の `SortKeyPosition` プロパティを 1 に設定します。 これは、ColumnA が最初に並べ替えられる列で、並べ替えが昇順で行われることを示します。  
  
    -   ColumnB の `SortKeyPosition` プロパティを -2 に設定します。 これは、ColumnB が 2 番目に並べ替えられる列で、並べ替えが降順で行われることを示します。  
  
    -   設定、 `SortKeyPosition` ColumnC のプロパティを 3。 これは、ColumnC が 3 番目に並べ替えられる列で、並べ替えが昇順で行われることを示します。  
  
9. 並べ替える列ごとに、手順 8. を繰り返します。  
  
10. [**OK**] をクリックします。  
  
11. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [マージ変換](merge-transformation.md)   
 [マージ結合変換](merge-join-transformation.md)   
 [Integration Services の変換](integration-services-transformations.md)   
 [Integration Services のパス](../integration-services-paths.md)   
 [データ フロー タスク]((../../control-flow/data-flow-task.md)  
  
  
