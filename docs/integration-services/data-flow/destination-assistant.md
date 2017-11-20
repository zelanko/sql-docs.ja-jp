---
title: "変換先アシスタント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.destinationassistant.f1
- sql13.DTS.DESIGNER.DESTINATIONASSIST.F1
ms.assetid: 10a40921-a2c2-4ac8-be28-311f8500fbf6
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: aebe1dfa1046bddfa86e48aecdd68930caf3285c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="destination-assistant"></a>デスティネーション アシスタント
  変換先アシスタント コンポーネントを使用すると、変換先コンポーネントおよび接続マネージャーを作成できます。 このコンポーネントは、SSIS ツールボックスの **[お気に入り]** セクションにあります。  
  
> [!NOTE]  
>  変換先アシスタントは、Integration Services 接続プロジェクトと対応するウィザードに置き換わるものです。  

## <a name="add-a-destination-with-destination-assistant"></a>変換先アシスタントによる変換先を追加します。
このトピックでは、変換先アシスタントを使用して新しい変換先を追加する手順について説明します。また、 **[新しい変換先の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換先アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。  

1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、変換先コンポーネントを追加する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **変換先アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。**[新しい変換先の追加]** ダイアログ ボックスが表示されます。 次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。  
  
3.  **[種類]** 一覧で、変換先の種類を選択します。  
  
4.  既存の接続マネージャーを選択して、**接続マネージャー**を一覧表示または選択**\<新規 >**新しい接続マネージャーを作成します。  
  
5.  既存の接続マネージャーを選択した場合は、**[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。 変換先と接続マネージャーがデータ フローに追加されます。  
  
6.  クリックした場合**\<新規 >** 、新しい接続マネージャーを作成、表示、**接続マネージャー**  ダイアログ ボックスは、接続のパラメーターを指定することができます。 新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。 
  
## <a name="add-new-destination-dialog-box"></a>新しい変換先 ダイアログ ボックスを追加します。
次の表に、オプションで使用できる、 **[新しい変換先**] ダイアログ ボックス。  
  
|オプション|Description|  
|------------|-----------------|  
|型|変換先の種類を選択します。|  
|接続マネージャー|既存の接続マネージャーを選択するかクリックして**\<新規 >**新しい接続マネージャーを作成します。|  
|インストールされているもののみを表示する|インストールされている変換先のみを表示するかどうかを指定します。|  
|OK|変更を保存し、後続のダイアログ ボックスを開いてその他のオプションを構成する場合にクリックします。|  

