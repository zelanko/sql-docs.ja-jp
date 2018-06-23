---
title: 'レッスン 1: Windows Azure ストレージ アカウントとコンテナーの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9c4a2fb1db64456fe63bc814adda8278b253937a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175057"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>レッスン 1: Windows Azure ストレージ アカウントとコンテナーを作成する
  Windows Azure ストレージへの SQL Server データ ファイルの格納を開始する前に、最初に Windows Azure ストレージ アカウント、BLOB コンテナー、および共有アクセス署名を作成する必要があります。 レッスン 1 では、Windows Azure 管理ポータルにログインし、ストレージ アカウント、BLOB コンテナー、および Shared Access Signature を作成する手順について説明します。  
  
 既定では、ストレージ アカウントの所有者だけがそのアカウント内の BLOB、テーブル、およびキューにアクセスすることができます。 この新しい SQL Server の機能強化を使用して、ストレージ アカウント アクセス キーを共有しないで、これらのリソースにアクセスするには、次の操作をする必要があります。  
  
-   コンテナーの権限をプライベートに設定します。  
  
-   Shared Access Signature を作成します。 これにより、リソースを利用可能な期間とクライアントに必要な権限を指定して、コンテナー、BLOB、テーブル、またはキュー リソースに対する制限付きアクセスをデリゲートすることができます。  
  
-   保存されたアクセス ポリシーを使用して、コンテナーまたは BLOB の Shared Access Signature を管理します。 保存されたアクセス ポリシーは、Shared Access Signatures をコントロールするもう 1 つの手段となり、それを取り消す直接的な手段にもなります。  
  
 詳細については、次を参照してください。 [Windows Azure ストレージ リソースへのアクセスの管理](http://msdn.microsoft.com/library/windowsazure/ee393343.aspx)です。  
  
## <a name="create-storage-account"></a>ストレージ アカウントの作成  
 Windows Azure 管理ポータルにストレージ アカウントを作成するには、次の手順を実行します。  
  
1.  ログインに、 [Windows Azure 管理ポータル](https://manage.windowsazure.com)アカウントを使用します。 Windows Azure アカウントがないを参照してください。 [Windows Azure 無料評価版](http://www.windowsazure.com/pricing/free-trial/)です。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  ステップ バイ ステップの指示を使用して[ストレージ アカウントの作成](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/)です。 Windows Azure 機能内の SQL Server データ ファイルで使用するストレージ アカウントを作成するときは、地理的レプリケーションを選択解除または無効にする必要があることに注意してください。 これは、地理的レプリケーションに参加している複数の BLOB では、書き込みの順序が保証されていないためです。 ストレージ アカウントで地理的レプリケーションが実行されていて、復旧が必要になった場合、データが破損します。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Blob コンテナーを作成します。  
 Windows Azure には、一連の BLOB をグループ化するコンテナーが用意されています。 すべての BLOB は 1 つのコンテナーに存在する必要があります。 ストレージ アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。 コンテナーには、BLOB を無制限に格納できます。 ストレージのサイズ制限に関する最新情報については、次を参照してください。 [.NET で Windows Azure Blob ストレージ サービスを使用する方法](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)です。  
  
 Windows Azure でコンテナーを作成するには、次の手順を実行します。  
  
1.  ログインに、 [Windows Azure 管理ポータル](https://manage.windowsazure.com)です。  
  
2.  ストレージ アカウントを選択し、をクリックして、**コンテナー**  タブでをクリックし、**コンテナーの追加**画面の下部には、新しいダイアログ ボックスを表示します。  
  
3.  コンテナーの名前を入力します。  
  
4.  選択**プライベート**の**アクセスの種類**です。 アクセスをプライベートに設定すると、コンテナーと BLOB データを読み取ることができるのは Windows Azure アカウントの所有者だけになります。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  コンテナーをプログラムで作成するために、REST API を使用することもできます。 詳細については、次を参照してください。[コンテナーの作成](http://msdn.microsoft.com/library/windowsazure/dd179468.aspx)、さらに[Windows Azure ストレージ サービス REST API リファレンス](http://msdn.microsoft.com/library/windowsazure/dd179355.aspx)です。  
  
 **次のレッスン:**  
  
 [レッスン 2:コンテナーのポリシーを作成し、Shared Access Signature を生成する&#40;SAS&#41;キー](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  