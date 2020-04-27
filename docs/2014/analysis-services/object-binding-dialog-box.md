---
title: '[オブジェクトのバインド] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cc86a5712dae9c231fa6e03d86a82d7dc172a75
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072186"
---
# <a name="object-binding-dialog-box"></a>[オブジェクトのバインド] ダイアログ ボックス
  **の** [オブジェクトのバインド] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトのプロパティとデータ ソース ビューのテーブルまたは列の間のバインドを定義できます。 **[オブジェクトのバインド]** ダイアログ ボックスを表示するには、 **の** [プロパティ] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ウィンドウで **オブジェクトの次のプロパティの値に対して、ドロップダウン リストから** [(新規)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を選択します。  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>オプション  
 **バインドの種類**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトに対して使用するバインドを選択します。 次の種類のバインドを使用できます。  
  
 [列のバインド]  
 オブジェクトをデータ ソース ビュー内の既存のテーブルおよび列にバインドします。  
  
 [列の生成]  
 データ ソース ビュー内で新しい列を定義して、列のバインドを関連付けることを示します。  
  
> [!NOTE]  
>   このオプションを選択した場合は、 **オブジェクトを配置する前に** スキーマ生成ウィザード [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] を実行する必要があります。  
  
 [行のバインド]  
 オブジェクトをファクト テーブルの行にバインドします。ファクト テーブルで処理される行の数に基づくカウント メジャーに役立ちます。  
  
 **ソース テーブル**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトに関連付けられているデータ ソース ビュー内のテーブルの一覧を表示します。  
  
 **ソース列**  
 **[基になるテーブル]** で選択されているテーブル内の列の一覧を表示します。  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
