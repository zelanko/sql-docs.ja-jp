---
title: ドメイン管理アクティビティの終了 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c9f53d3878ec6f5eb9c0996d7162fed792bf4930
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033369"
---
# <a name="end-the-domain-management-activity"></a>ドメイン管理アクティビティの終了
  このトピックでは、[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のドメイン管理アクティビティを完了、終了、またはキャンセルする方法について説明します。 ドメイン管理はウィザードで実行されないため、以下で説明する制御はドメイン管理アクティビティのどのページからでも使用できます。  
  
## <a name="end-domain-management"></a>ドメイン管理の終了  
 **[完了]**  
 クリックすると、ドメイン管理が完了します。 ポップアップ画面で、次のいずれかを選択します。  
  
-   **[はい - ナレッジ ベースを発行して終了]**: 現在のユーザーまたは他のユーザーに対してナレッジ ベースが発行されます。 ナレッジ ベースはロックされず、(ナレッジ ベース テーブルの) ナレッジ ベースの状態が空白に設定されます。ドメイン管理アクティビティとナレッジ検出アクティビティの両方を使用できるようになります。 [ナレッジ ベースを開く] 画面に戻ります。  
  
-   **[いいえ - 作業内容をナレッジ ベースに保存して終了]**: 作業内容が保存され、ナレッジ ベースはロックされたままになります。ナレッジ ベースの状態は [作業中] に設定されます。 ドメイン管理アクティビティとナレッジ検出アクティビティの両方を使用できるようになります。 ホーム ページに戻ります。  
  
-   **[キャンセル - 現在の画面を継続]**: ポップアップが閉じ、[ドメイン管理] 画面に戻ります。  
  
 **Cancel**  
 クリックすると、ドメイン管理アクティビティが終了して作業内容が破棄され、DQS ホーム ページに戻ります。  
  
 **Close**  
 クリックすると、作業内容が保存され、DQS ホーム ページに戻ります。 ナレッジ ベースがロックされ、 **[ナレッジ ベースを開く]** 画面のナレッジ ベース テーブルのナレッジ ベースの状態が **[ドメイン管理]** になります。 **[閉じる]** をクリックした後でナレッジ検出アクティビティを実行するには、 **[ドメイン管理]** 画面に戻り、 **[完了]** をクリックします。次に、ナレッジ ベースを発行する場合は **[はい]** を、作業内容をナレッジ ベースに保存して終了する場合は **[いいえ]** をクリックします。  ロックされたナレッジ ベースを開く方法の詳細については、「 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。  
  
  
