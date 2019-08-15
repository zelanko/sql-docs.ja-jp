---
title: レッスン 1:Windows Azure Storage アカウントとコンテナーを作成する |Microsoft Docs
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
ms.openlocfilehash: 9047c517fe4766ab5c3792d2fa2bf92eb7197965
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028505"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>レッスン 1:Windows Azure ストレージ アカウントとコンテナーを作成する
  Windows Azure ストレージへの SQL Server データ ファイルの格納を開始する前に、最初に Windows Azure ストレージ アカウント、BLOB コンテナー、および共有アクセス署名を作成する必要があります。 レッスン 1 では、Windows Azure 管理ポータルにログインし、ストレージ アカウント、BLOB コンテナー、および Shared Access Signature を作成する手順について説明します。  
  
 既定では、ストレージ アカウントの所有者だけがそのアカウント内の BLOB、テーブル、およびキューにアクセスすることができます。 この新しい SQL Server の機能強化を使用して、ストレージ アカウント アクセス キーを共有しないで、これらのリソースにアクセスするには、次の操作をする必要があります。  
  
-   コンテナーの権限をプライベートに設定します。  
  
-   Shared Access Signature を作成します。 これにより、リソースを利用可能な期間とクライアントに必要な権限を指定して、コンテナー、BLOB、テーブル、またはキュー リソースに対する制限付きアクセスをデリゲートすることができます。  
  
-   保存されたアクセス ポリシーを使用して、コンテナーまたは BLOB の Shared Access Signature を管理します。 保存されたアクセス ポリシーは、Shared Access Signatures をコントロールするもう 1 つの手段となり、それを取り消す直接的な手段にもなります。  
  
 詳細については、「 [Windows Azure Storage リソースへのアクセスの管理](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx)」を参照してください。  
  
## <a name="create-storage-account"></a>ストレージ アカウントの作成  
 Windows Azure 管理ポータルにストレージ アカウントを作成するには、次の手順を実行します。  
  
1.  アカウントを使用して[Windows Azure 管理ポータル](https://manage.windowsazure.com)にログインします。 Windows Azure アカウントを持っていない場合は、「 [Windows azure 無料評価版](http://www.windowsazure.com/pricing/free-trial/)」を参照してください。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  詳細な手順に従って、[ストレージアカウントを作成](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)します。 Windows Azure 機能内の SQL Server データ ファイルで使用するストレージ アカウントを作成するときは、地理的レプリケーションを選択解除または無効にする必要があることに注意してください。 これは、地理的レプリケーションに参加している複数の BLOB では、書き込みの順序が保証されていないためです。 ストレージ アカウントで地理的レプリケーションが実行されていて、復旧が必要になった場合、データが破損します。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Blob コンテナーを作成する  
 Windows Azure には、一連の BLOB をグループ化するコンテナーが用意されています。 すべての BLOB は 1 つのコンテナーに存在する必要があります。 ストレージ アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。 コンテナーには、BLOB を無制限に格納できます。 ストレージサイズの制限に関する最新情報については、「 [.net で Windows Azure Blob Storage サービスを使用する方法](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/)」を参照してください。  
  
 Windows Azure でコンテナーを作成するには、次の手順を実行します。  
  
1.  [Windows Azure 管理ポータル](https://manage.windowsazure.com)にログインします。  
  
2.  ストレージアカウントを選択し、[**コンテナー** ] タブをクリックし、画面の下部にある [**コンテナーの追加**] をクリックすると、新しいダイアログボックスが開きます。  
  
3.  コンテナーの名前を入力します。  
  
4.  [アクセスの**種類**] で [**プライベート**] を選択します。 アクセスをプライベートに設定すると、コンテナーと BLOB データを読み取ることができるのは Windows Azure アカウントの所有者だけになります。  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  コンテナーをプログラムで作成するために、REST API を使用することもできます。 詳細については、「 [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) 」と「 [Windows Azure Storage Services REST API リファレンス](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx)」を参照してください。  
  
 **次のレッスン:**  
  
 [レッスン 2:コンテナーでポリシーを作成し、Shared Access Signature &#40;の SAS&#41;キーを生成する](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  
