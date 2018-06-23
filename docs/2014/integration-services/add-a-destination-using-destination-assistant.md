---
title: 変換先アシスタントを使用して変換先の追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 88d942ea38004d6d4085b73a4f2967a9a2e68705
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176236"
---
# <a name="add-a-destination-using-destination-assistant"></a>デスティネーション アシスタントを使用して変換先を追加する
  このトピックでは、変換先アシスタントを使用して新しい変換先を追加する手順について説明します。また、**[新しい変換先の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換先アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a>変換先アシスタントを使用して変換先を追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変換先コンポーネントを追加する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **変換先アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。**[新しい変換先の追加]** ダイアログ ボックスが表示されます。 次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。  
  
3.  **[種類]** 一覧で、変換先の種類を選択します。  
  
4.  **[接続マネージャー]** 一覧で既存の接続マネージャーを選択するか、**[\<新規作成>]** を選択して新しい接続マネージャーを作成します。  
  
5.  既存の接続マネージャーを選択した場合は、**[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。 変換先と接続マネージャーがデータ フローに追加されます。  
  
6.  **[\<新規作成>]** をクリックして新しい接続マネージャーを作成する場合は、**[接続マネージャー]** ダイアログ ボックスが表示され、接続のパラメーターを指定できます。 新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。  
  
  