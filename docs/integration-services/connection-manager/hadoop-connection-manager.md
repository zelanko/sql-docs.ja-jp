---
title: "Hadoop 接続マネージャー | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ssis.designer.hadoopconn.f1
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c4bf82dad09b90f672e52947267ddf92fbdb984
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="hadoop-connection-manager"></a>Hadoop 接続マネージャー
  Hadoop 接続マネージャーは、SSIS パッケージがプロパティに指定された値を使用して Hadoop クラスターに接続することを可能にします。  
  
## <a name="configure-the-hadoop-connection-manager"></a>Hadoop 接続マネージャーの構成  
  
1.  **[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[Hadoop]**を選択し、 **[追加]**をクリックします。 **[Hadoop Connection Manager Editor]** (Hadoop Connection 接続マネージャー エディター) ダイアログ ボックスが表示されます。  
  
2.  左側のウィンドウで **[WebHCat]** (WebHCat) または **[WebHDFS]** (WebHDFS) タブを選択し、関連する Hadoop クラスター情報を構成します。  
  
3.  Hive または Pig ジョブを Hadoop で起動するために **WebHCat** オプションを有効にする場合は、次の操作を行います。  
  
    1.  **[WebHCat Host]**(WebHCat ホスト) に、WebHCat サービスをホストするサーバーを入力します。  
  
    2.  **[WebHCat Port]**(WebHCat ポート) に、WebHCat サービスのポートを入力します (既定値は 50111 です)。  
  
    3.  WebHCat サービスにアクセスするときに使用する **認証** 方法を選択します。 使用できる値は、 **[基本]** と **[Kerberos]**です。  
  
         ![基本認証が指定された Hadoop 接続マネージャー エディター](../../integration-services/connection-manager/media/hadoop-cm-basic.png "基本認証が指定された Hadoop 接続マネージャー エディター")  
  
         ![Kerberos 認証が指定された Hadoop 接続マネージャー エディター](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Kerberos 認証が指定された Hadoop 接続マネージャー エディター")  
  
    4.  **[WebHCat User]**(WebHCat ユーザー) に、WebHCat へのアクセスが許可されている **ユーザー** を入力します。  
  
    5.  **[Kerberos]** 認証を選択した場合は、ユーザーの **パスワード** と **ドメイン**を入力します。  
  
4.  HDFS との間でデータをコピーするために **WebHDFS** オプションを有効にする場合は、次の操作を行います。  
  
    1.  **[WebHDFS Host]**(WebHDFS ホスト) に、WebHDFS サービスをホストするサーバーを入力します。  
  
    2.  **[WebHDFS Port]**(WebHDFS ポート) に、WebHDFS サービスのポートを入力します (既定値は 50070 です)。  
  
    3.  WebHDFS サービスにアクセスするときに使用する **認証** 方法を選択します。 使用できる値は、 **[基本]** と **[Kerberos]**です。  
  
    4.  **[WebHDFS User]**(WebHDFS ユーザー) に、HDFS へのアクセスが許可されているユーザーを入力します。  
  
    5.  **[Kerberos]** 認証を選択した場合は、ユーザーの **パスワード** と **ドメイン**を入力します。  
  
5.  **[接続テスト]** をクリックして接続をテストします。 (有効にした接続のみがテストされます)。  
  
6.  **[OK]** をクリックして、ダイアログ ボックスを閉じます。  
  
## <a name="see-also"></a>参照  
 [Hadoop Hive Task](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Hadoop Pig Task](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Hadoop ファイル システム タスク](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  
