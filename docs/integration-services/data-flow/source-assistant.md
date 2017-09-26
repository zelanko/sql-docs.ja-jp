---
title: "ソース アシスタント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sourceassistant.f1
- sql13.dts.designer.addNewSource.f1
ms.assetid: 5ca9d821-7d61-4727-9133-5f9cb485c7f3
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9b7406edf9f7234db739730473772d77c42399ec
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="source-assistant"></a>ソース アシスタント
  変換元アシスタント コンポーネントを使用すると、変換元コンポーネントおよび接続マネージャーを作成できます。 このコンポーネントは、SSIS ツールボックスの **[お気に入り]** セクションにあります。  
  
> [!NOTE]  
>  変換元アシスタントは、Integration Services 接続プロジェクトと対応するウィザードに置き換わるものです。  
  
## <a name="add-a-source-with-source-assistant"></a>変換元アシスタントを持つソースを追加します。
このセクションでは、変換元アシスタントを使用して、新しいソースを追加する手順を説明しで使用できるオプションも示します、**新しいソースの追加**ダイアログで、ときにドラッグ アンド ドロップした変換元アシスタントを SSIS デザイナーが表示されます。  

1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、変換元コンポーネントを追加する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **変換元アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。**[新しい変換元の追加]** ダイアログ ボックスが表示されます。 次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。  
  
3.  **[種類]** 一覧で、変換先の種類を選択します。  
  
4.  既存の接続マネージャーを選択して、**接続マネージャー**を一覧表示または選択**\<新規 >**新しい接続マネージャーを作成します。  
  
5.  既存の接続マネージャーを選択した場合は、**[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。 変換先と接続マネージャーがデータ フローに追加されます。  
  
6.  クリックした場合**\<新規 >** 、新しい接続マネージャーを作成、表示、**接続マネージャー**  ダイアログ ボックスは、接続のパラメーターを指定することができます。 新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。  

## <a name="add-new-source-dialog-box"></a>新しいソース ダイアログ ボックスを追加します。
次の表で使用できるオプションの一覧、**新しいソースの追加** ダイアログ ボックス。  
  
|オプション|Description|  
|------------|-----------------|  
|型|接続先のソースの種類を選択します。|  
|接続マネージャー|既存の接続マネージャーを選択するかクリックして**\<新規 >**新しい接続マネージャーを作成します。|  
|インストールされているもののみを表示する|インストールされているソースのみを表示するかどうかを指定します。|  
|OK|変更を保存し、後続のダイアログ ボックスを開いてその他のオプションを構成する場合にクリックします。| 
  
