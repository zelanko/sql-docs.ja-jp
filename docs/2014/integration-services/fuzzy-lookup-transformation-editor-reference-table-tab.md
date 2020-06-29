---
title: '[あいまい参照変換エディター] ([参照テーブル] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.referencetable.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 451f4e7d-1c8e-4784-b540-df0806509bf1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb86e4a6382095bb8bb0edc744fe6d16650581fd
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425209"
---
# <a name="fuzzy-lookup-transformation-editor-reference-table-tab"></a>[あいまい参照変換エディター] ([参照テーブル] タブ)
  **[あいまい参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブを使用すると、参照に使用する変換元テーブルとインデックスを指定できます。 参照データ ソースは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースのテーブルである必要があります。  
  
> [!NOTE]  
>  あいまい参照変換では、参照テーブルの作業用コピーが作成されます。 以降に説明するインデックスは、通常の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インデックスではなく、特別なテーブルを使用してこの作業用テーブルに作成されるものです。 **[保存されたインデックスを維持する]** を選択しないと、既存の変換元テーブルは変更されません。 この場合、参照テーブルに加えられた変更に基づいて作業用テーブルと参照インデックス テーブルを更新するトリガーが、参照テーブルに作成されます。  
  
> [!NOTE]  
>  `Exhaustive` `MaxMemoryUsage` あいまい参照変換のおよびプロパティは、[**あいまい参照変換エディター**] では使用できませんが、**詳細エディター**を使用して設定できます。 また、の100より大きい値は、 `MaxOutputMatchesPerInput` **詳細エディター**でのみ指定できます。 これらのプロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」の「あいまい参照変換」を参照してください。  
  
 あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **OLE DB 接続マネージャー**  
 一覧から既存の OLE DB 接続マネージャーを選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **[新しいインデックスを生成する]**  
 参照に使用する新しいインデックスを作成するように指定します。  
  
 **[参照テーブル名]**  
 参照テーブルとして使用する既存のテーブルを選択します。  
  
 **[新しいインデックスを保存する]**  
 新しい参照インデックスを保存する場合に、このオプションを選択します。  
  
 **[新しいインデックス名]**  
 新しい参照インデックスを保存するように指定した場合、そのインデックスの名前を入力します。  
  
 **[保存されたインデックスを維持する]**  
 新しい参照インデックスを保存するように指定した場合、そのインデックスを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でも維持するかどうかを指定します。  
  
> [!NOTE]  
>  **[あいまい参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブで **[保存されたインデックスを維持する]** を選択すると、変換ではマネージド ストアド プロシージャを使用してインデックスを維持します。 これらのマネージド ストアド プロシージャは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の共通言語ランタイム (CLR) 統合機能を使用します。 既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の CLR 統合は無効です。 **[保存されたインデックスを維持する]** 機能を使用するには、CLR 統合を有効にする必要があります。 詳細については、「 [CLR 統合の有効化](../relational-databases/clr-integration/clr-integration-enabling.md)」を参照してください。  
>   
>  **[保存されたインデックスを維持する]** オプションは CLR 統合を必要とするため、この機能を使用できるのは、CLR 統合が有効になっている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスの参照テーブルを選択した場合だけです。  
  
 **[既存のインデックスを使用する]**  
 参照に既存のインデックスを使用するように指定します。  
  
 **[既存のインデックスの名前]**  
 以前に作成した参照インデックスを一覧から選択します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換エディター &#40;[列] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [[あいまい参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
