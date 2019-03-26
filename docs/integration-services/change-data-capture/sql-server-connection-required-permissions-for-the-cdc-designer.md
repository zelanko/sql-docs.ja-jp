---
title: CDC デザイナーで使用する SQL Server 接続に必要な権限 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b9a95743de7e75620cc1f3b0d07b2d9b42a878f3
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290055"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a>CDC デザイナーで使用する SQL Server 接続に必要な権限
  CDC デザイナー コンソールのタスクを実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続情報が必要です。 このトピックでは、 **との接続を設定するために** [SQL Server への接続] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ダイアログ ボックスで指定できる情報について説明します。  
  
 **‭[SQL Server への接続]** ダイアログ ボックスは必要なときに開きます。たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続情報がない場合や、情報は存在しても接続に必要な権限がない場合などです。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続が必要となる各種のタスクと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン/ユーザーに必要な権限について説明します。  
  
|タスク|最低限の権限|  
|----------|-------------------------|  
|関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用した CDC サービスおよびインスタンスの一覧表示|`db_datareader` ロール|  
|CDC インスタンスの開始/停止|`db_datareader` ロールと `db_datawriter` ロール|  
|CDC インスタンスの状態の表示|`db_owner` ロール|  
|新しい Oracle CDC インスタンス データベースの作成|`dbcreator` 固定サーバー ロール|  
|新しい Oracle CDC インスタンスの作成|`db_datareader` ロール<br /><br /> `db_owner` ロール|  
|配置スクリプトの取得|`db_datareader` ロールと `db_datawriter` ロール<br /><br /> `db_owner` ロール|  
|構成の変更およびキャプチャ インスタンスの追加/削除|`db_datareader` ロールと `db_datawriter` ロール<br /><br /> `db_owner` ロール|  
  
## <a name="see-also"></a>参照  
 [CDC デザイナー コンソールへのアクセス](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [インスタンスの作成のための SQL サーバー接続](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  
