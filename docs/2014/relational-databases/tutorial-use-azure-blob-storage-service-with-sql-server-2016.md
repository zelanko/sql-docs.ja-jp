---
title: 'チュートリアル: SQL Server データ ファイルを Windows Azure ストレージ サービス |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd793aad219d8e65a787dd3d872046df00cca414
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177483"
---
# <a name="tutorial-sql-server-data-files-in-windows-azure-storage-service"></a>チュートリアル: Windows Azure ストレージ サービス内の SQL Server データ ファイル
  Windows Azure ストレージ サービス内の SQL Server データ ファイルのチュートリアルにようこそ。 このチュートリアルにより、Windows Azure BLOB ストレージ サービスに SQL Server データ ファイルを直接格納する方法について把握できます。  
  
 Windows Azure BLOB ストレージ サービスに対する SQL Server 統合のサポートは、SQL Server 2014 の拡張機能です。 この機能を使用する利点と機能の概要についてを参照してください[Windows Azure で SQL Server データ ファイル](databases/sql-server-data-files-in-microsoft-azure.md)です。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、複数のレッスンに分けて、Windows Azure ストレージ サービスに SQL Server データ ファイルを格納する方法を説明します。 各レッスンでは特定のタスクに重点を置きます。 まず、Windows Azure でストレージ アカウントおよびコンテナーを作成する方法を学習します。 次に、SQL Server を Windows Azure ストレージと統合できるようにするために SQL Server 資格情報を作成する方法を学習します。 その後、Windows Azure ストレージにデータベースを直接作成します。 さらに、暗号化、移行、およびバックアップと復元のシナリオを示します。  
  
 このチュートリアルは、次の 9 つのレッスンで構成されています。  
  
 **[レッスン 1: Windows Azure ストレージ アカウントとコンテナーを作成します。](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 このレッスンでは、Windows Azure ストレージ アカウントおよびコンテナーを作成します。  
  
 **[レッスン 2 です。コンテナーのポリシーを作成し、Shared Access Signature を生成する&#40;SAS&#41;キー](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 このレッスンでは、BLOB コンテナーのポリシーを作成し、Shared Access Signature を生成します。  
  
 **[レッスン 3: SQL Server 資格情報を作成します。](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 このレッスンでは、Windows Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
 **[レッスン 4: Windows Azure ストレージにデータベースを作成します。](../relational-databases/lesson-3-database-backup-to-url.md)**  
 このレッスンでは、CREATE Database FILENAME オプションを使用して、Windows Azure ストレージにデータベースを作成します。  
  
 **[レッスン 5 です。&#40;オプション&#41;TDE を使用して、データベースの暗号化](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 このレッスンでは、透過的なデータ暗号化 (TDE) およびサーバー証明書を使用してデータベースを暗号化します。  
  
 **[レッスン 6: ソースからのデータベースの移行のターゲット コンピューターに Windows Azure をオンプレミスのコンピューター](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 このレッスンでは、CREATE DATABASE FOR ATTACH オプションを使用して、データベースを内部設置型から Windows Azure の仮想マシンに移行します。  
  
 **[レッスン 7: Windows Azure ストレージへのデータ ファイルを移動します。](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 このレッスンでは、ALTER DATABASE ステートメントを使用して、データ ファイルを Windows Azure ストレージに移動します。  
  
 **[レッスン 8: Windows Azure ストレージにデータベースを復元します。](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 このレッスンでは、RESTORE Database MOVE オプションを使用して、Windows Azure ストレージにデータベースを復元します。  
  
 **[レッスン 9 です。Windows Azure ストレージからデータベースを復元します。](lesson-8-restore-as-new-database-from-log-backup.md)**  
 このレッスンでは、RESTORE Database MOVE オプションを使用して、Windows Azure ストレージからデータベースを復元します。  
  
## <a name="see-also"></a>参照  
 [Windows Azure 内の SQL Server データ ファイル](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  