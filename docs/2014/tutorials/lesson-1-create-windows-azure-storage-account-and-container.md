---
title: レッスン 1:Windows Azure ストレージ アカウントとコンテナーの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8a1f8cef9f29c856ab0bc02480221e583a0078f3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039933"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>レッスン 1:Windows Azure ストレージ アカウントとコンテナーを作成します。
  Windows Azure ストレージへの SQL Server データ ファイルの格納を開始する前に、最初に Windows Azure ストレージ アカウント、BLOB コンテナー、および共有アクセス署名を作成する必要があります。 レッスン 1 では、Windows Azure 管理ポータルにログインし、ストレージ アカウント、BLOB コンテナー、および Shared Access Signature を作成する手順について説明します。  
  
 既定では、ストレージ アカウントの所有者だけがそのアカウント内の BLOB、テーブル、およびキューにアクセスすることができます。 この新しい SQL Server の機能強化を使用して、ストレージ アカウント アクセス キーを共有しないで、これらのリソースにアクセスするには、次の操作をする必要があります。  
  
-   コンテナーの権限をプライベートに設定します。  
  
-   Shared Access Signature を作成します。 これにより、リソースを利用可能な期間とクライアントに必要な権限を指定して、コンテナー、BLOB、テーブル、またはキュー リソースに対する制限付きアクセスをデリゲートすることができます。  
  
-   保存されたアクセス ポリシーを使用して、コンテナーまたは BLOB の Shared Access Signature を管理します。 保存されたアクセス ポリシーは、Shared Access Signatures をコントロールするもう 1 つの手段となり、それを取り消す直接的な手段にもなります。  
  
 詳細については、次を参照してください。 [Windows Azure ストレージ リソースへのアクセスの管理](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)します。  
  
## <a name="create-storage-account"></a>ストレージ アカウントの作成  
 Windows Azure 管理ポータルにストレージ アカウントを作成するには、次の手順を実行します。  
  
1.  ログイン、 [Windows Azure 管理ポータル](https://manage.windowsazure.com)アカウントを使用します。 Windows Azure アカウントがないを参照してください。 [Windows Azure 無料試用版](http://www.windowsazure.com/pricing/free-trial/)します。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  ステップ バイ ステップの手順を使用[ストレージ アカウントの作成](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/)です。 Windows Azure 機能内の SQL Server データ ファイルで使用するストレージ アカウントを作成するときは、地理的レプリケーションを選択解除または無効にする必要があることに注意してください。 これは、地理的レプリケーションに参加している複数の BLOB では、書き込みの順序が保証されていないためです。 ストレージ アカウントで地理的レプリケーションが実行されていて、復旧が必要になった場合、データが破損します。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Blob コンテナーを作成します。  
 Windows Azure には、一連の BLOB をグループ化するコンテナーが用意されています。 すべての BLOB は 1 つのコンテナーに存在する必要があります。 ストレージ アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。 コンテナーには、BLOB を無制限に格納できます。 ストレージ サイズの制限に関する最新情報については、次を参照してください。 [.NET で Windows Azure Blob ストレージ サービスを使用する方法](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)します。  
  
 Windows Azure でコンテナーを作成するには、次の手順を実行します。  
  
1.  ログイン、 [Windows Azure 管理ポータル](https://manage.windowsazure.com)します。  
  
2.  ストレージ アカウントを選択して、、**コンテナー**  タブでをクリックし、**コンテナーの追加**を画面の下部には、新しい ダイアログ ボックスを開きます。  
  
3.  コンテナーの名前を入力します。  
  
4.  選択**プライベート**の**アクセスの種類**します。 アクセスをプライベートに設定すると、コンテナーと BLOB データを読み取ることができるのは Windows Azure アカウントの所有者だけになります。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  コンテナーをプログラムで作成するために、REST API を使用することもできます。 詳細については、次を参照してください。[コンテナーの作成](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx)また[Windows Azure ストレージ サービス REST API リファレンス](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)します。  
  
 **次のレッスン:**  
  
 [レッスン 2:コンテナーのポリシーを作成し、Shared Access Signature の生成&#40;SAS&#41;キー](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  
