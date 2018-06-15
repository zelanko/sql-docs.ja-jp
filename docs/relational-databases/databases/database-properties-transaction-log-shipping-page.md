---
title: '[データベースのプロパティ] ([トランザクション ログの配布] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a84c96b1f1699bc2373e40a404c1c0b07d7e91a3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32927407"
---
# <a name="database-properties-transaction-log-shipping-page"></a>[データベースのプロパティ] ([トランザクション ログの配布] ページ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このページを使用すると、データベースのログ配布のプロパティを構成および変更できます。  
  
 ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[ログ配布構成のプライマリ データベースとして有効にする]**  
 このデータベースをログ配布のプライマリ データベースとして有効にします。 オンにした場合は、このページの残りのオプションを構成します。 このチェック ボックスをオフにした場合、このデータベースのログ配布構成は削除されます。  
  
 **[バックアップの設定]**  
 **[バックアップの設定]** をクリックすると、バックアップ スケジュール、場所、警告、およびアーカイブ パラメーターを構成できます。  
  
 **[バックアップ スケジュール]**  
 プライマリ データベースに対して現在選択されているバックアップ スケジュールを表示します。 これらの設定を変更するには、 **[バックアップの設定]** をクリックします。  
  
 **[最後に作成したバックアップ]**  
 プライマリ データベースの最新のトランザクション ログ バックアップの作成日付を示します。  
  
 **[セカンダリ サーバー インスタンスとデータベース]**  
 このプライマリ データベースに対して現在構成されているセカンダリ サーバーおよびセカンダリ データベースを表示します。 セカンダリ データベースに関連付けられているパラメーターを変更するには、データベースを強調表示し、 **[...]** をクリックします。  
  
 **[追加]**  
 このプライマリ データベースのログ配布構成にセカンダリ データベースを追加するには、 **[追加]** をクリックします。  
  
 **[削除]**  
 選択されているデータベースをこのログ配布構成から削除します。 データベースを選択してから、 **[削除]** をクリックします。  
  
 **[監視サーバー インスタンスを使用する]**  
 このログ配布構成に対して監視サーバー インスタンスを設定します。 監視サーバー インスタンスを指定するには、 **[監視サーバー インスタンスを使用する]** チェック ボックスをオンにし、 **[設定]** をクリックします。  
  
 **[監視サーバー インスタンス]**  
 このログ配布構成に対して現在構成されている監視サーバー インスタンスを示します。  
  
 **[設定]**  
 ログ配布構成に対して監視サーバー インスタンスを構成します。 この監視サーバー インスタンスを構成するには、 **[設定]** をクリックします。  
  
 **[スクリプトの構成]**  
 選択されているパラメーターを使用して、ログ配布を構成するためのスクリプトを生成します。 **[スクリプトの構成]** をクリックし、スクリプトの出力先を選択します。  
  
> [!IMPORTANT]  
>  セカンダリ データベースの設定スクリプトを生成するには、 **[セカンダリ データベースの設定]** ダイアログ ボックスを呼び出す必要があります。 このダイアログ ボックスを呼び出すことにより、セカンダリ サーバーに接続して、スクリプトの生成に必要なセカンダリ データベースの現在の設定を取得できます。  
  
## <a name="see-also"></a>参照  
 [ログ配布ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql.md)   
 [ログ配布テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
