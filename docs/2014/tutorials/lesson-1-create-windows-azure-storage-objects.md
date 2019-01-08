---
title: レッスン 1:Windows Azure ストレージ オブジェクトの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: d238284bb53e4ce6acc5d482ae66c0b21a760da6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53373794"
---
# <a name="lesson-1-create-windows-azure-storage-objects"></a>レッスン 1:Windows Azure ストレージ オブジェクトを作成します。
  クラウド記憶域に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップを作成する前に、まず、ストレージ アカウントを作成してから BLOB コンテナーを作成する必要があります。 レッスン 1 では、ストレージ アカウントと BLOB コンテナーを作成して、Windows Azure 管理ポータルへのログイン手順について説明します。  
  
## <a name="create-a-storage-account"></a>ストレージ アカウントを作成します。  
 Windows Azure 管理ポータルからストレージ アカウントを作成するには、次の手順を実行します。  
  
1.  アカウントを使用して Windows Azure 管理ポータルにログインします。 Windows Azure アカウントがない[3 か月間無料試用版の Windows Azure を参照してください。](https://go.microsoft.com/fwlink/?LinkId=271927)します。  
  
     ![Windows Azure のログイン画面](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Windows Azure のログイン画面")  
  
2.  詳細なステップ バイ ステップの指示に従って[ここ](https://go.microsoft.com/fwlink/?LinkId=271926)、ストレージ アカウントを作成します。  
  
3.  前の手順で作成したストレージ アカウントを参照します。 Web ページの下部中央から次のようにクリックします。**キーの管理**します。 アカウント情報が表示されます。 ストレージ アカウント名とアクセス キーをコピーします。 この情報は、SQL の保存された資格情報を作成するために必要です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は、この情報を使用し、ストレージ アカウントにアクセスしてバックアップを作成します。  
  
     ![Windows Azure ストレージ アカウント キーのスクリーン ショット](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Windows Azure ストレージ アカウント キーのスクリーン ショット")  
  
    > [!NOTE]  
    >  ストレージ アカウントは、REST API を使用してプログラムで作成することもできます。 詳細については、次を参照してください。[ストレージ アカウントの作成](https://go.microsoft.com/fwlink/?LinkId=271928)です。  
  
### <a name="create-a-blob-container"></a>BLOB コンテナーの作成  
 コンテナーには、一連の BLOB をグループ化するコンテナーが用意されています。 すべての BLOB は 1 つのコンテナーに存在する必要があります。 アカウントには、コンテナーを無制限に含めることができますが、少なくとも 1 つのコンテナーが必要です。 コンテナーには、BLOB を無制限に格納できます。  
  
 コンテナーを作成するには、次の手順を実行します。  
  
1.  ストレージ アカウントを選択して、[、**コンテナー** ] タブでをクリックし、**コンテナーの追加**新しいダイアログ ボックスが表示される画面の下部にあります。  
  
     ![管理ポータルでコンテナーを作成する](../../2014/tutorials/media/backuptocloud.gif "管理ポータルでコンテナーの作成")  
  
2.  コンテナーの名前を入力します。 指定したコンテナー名をメモします。 この情報は、レッスン 3 と 4 の T-SQL ステートメントの URL (バックアップ ファイルのパス) で使用されます。  
  
3.  プライベートを選択**アクセスの種類**します。 バックアップ ファイルをセキュリティで保護するためのプライベート コンテナーを作成することをお勧めします。  
  
     ![新しい blob コンテナーを作成して](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "新しい blob コンテナーの作成")  
  
    > [!NOTE]  
    >  ストレージ アカウントへの認証は、パブリック コンテナーの作成を選択した場合でも、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元に必要です。  
    >   
    >  コンテナーは、REST API を使用してプログラムで作成することもできます。 詳細については、次を参照してください。[コンテナーの作成](https://go.microsoft.com/fwlink/?LinkId=271946)です。  
  
### <a name="next-lesson"></a>次のレッスン  
 [レッスン 2:SQL Server 資格情報を作成する](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)します。  
  
  
