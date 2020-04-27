---
title: 変換元アシスタントを使用してソースを追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e850b7c-4b89-42ad-b0a6-d63ac7cc9568
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b162ebfa6d888460b49f0877d634c88bba47464a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062137"
---
# <a name="add-a-source-using-source-assistant"></a>ソース アシスタントを使用してソースを追加する
  このトピックでは、変換元アシスタントを使用して新しい変換元を追加する手順について説明します。また、 **[新しい変換元の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換元アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。  
  
### <a name="to-use-source-assistant-to-add-a-source"></a>変換元アシスタントを使用して変換元を追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変換元コンポーネントを追加する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **変換元アシスタント**コンポーネントを SSIS ツールボックスから [**データフロー** ] タブにドラッグします。[**新しいソースの追加**] ダイアログボックスが表示されます。 次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。  
  
3.  **[種類]** 一覧で、変換先の種類を選択します。  
  
4.  [**接続**マネージャー] ボックスの一覧で既存の接続マネージャーを選択するか、[ ** \<新しい>** ] を選択して新しい接続マネージャーを作成します。  
  
5.  既存の接続マネージャーを選択した場合は、**[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。 変換先と接続マネージャーがデータ フローに追加されます。  
  
6.  [ ** \<新しい>** ] をクリックして新しい接続マネージャーを作成すると、[**接続マネージャー** ] ダイアログボックスが表示され、接続のパラメーターを指定できます。 新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。  
  
  
