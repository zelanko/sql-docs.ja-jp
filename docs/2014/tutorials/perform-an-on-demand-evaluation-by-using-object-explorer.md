---
title: オブジェクト エクスプ ローラーを使用して時評価を実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 55ca364c60c2b9fcca407561ed195035ce7205fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077235"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>オブジェクト エクスプローラーを使用した要求時評価の実行
  ここでは、オブジェクト エクスプローラーを使用して、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] の単一インスタンス上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に対して、ベスト プラクティス ポリシーの要求時評価を実行します。  
  
> [!NOTE]  
>  単一インスタンス上のポリシーの評価は、登録済みサーバーを通じて行うこともできます。 詳細については、次を参照してください。[登録済みサーバーを使用して、オンデマンド評価版を実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)です。  
  
## <a name="prerequisites"></a>前提条件  
 このレッスンでは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のバージョンを使用します。  
  
> [!NOTE]  
>  実行しているインスタンスに対してベスト プラクティス ポリシーのオンデマンドで評価を実行する[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、トピックの手順を使用する必要があります[登録済みサーバーを使用して、オンデマンド評価版を実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)です。  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>オブジェクト エクスプローラーを使用して要求時評価を実行するには  
  
1.  開始[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]に接続し、[!INCLUDE[ssDE](../includes/ssde-md.md)]です。  
  
2.  オブジェクト エクスプ ローラーで、**管理**、展開**ポリシーの管理**を右クリックして**ポリシー**をクリックし、**評価**です。  
  
    > [!NOTE]  
    >  既定では、ローカル インスタンスがポリシーのソースとして使用されます。 ベスト プラクティス ポリシーを以前にインポートしている場合は、作成済みのポリシーがあれば、それと共に一覧表示されます。 インポートしたベスト プラクティス ポリシーのいずれかを選択してをクリックして**評価**です。 ベスト プラクティス ポリシーをインポートしていない場合には、この手順を続行します。  
  
3.  **ポリシーの評価** ダイアログ ボックスで、**ソース**ボックスで、省略記号ボタン (**.**) ボタンをクリックします。  
  
4.  **ソースの選択** ダイアログ ボックスを選択できます。**ファイル**または**サーバー**を評価するポリシー ファイルのソースとして。 クリックすると**サーバー**、ローカルまたはリモート サーバー上のポリシー ベースの管理に以前インポートされたすべてのベスト プラクティス ポリシーのオンデマンドで評価を行うことができます。 このチュートリアルをクリックして**ファイル**、し評価する個々 のポリシー ファイルを選択します。 これを行うには、次の手順を実行します。  
  
    1.  をクリックして**ファイル**です。  
  
    2.  横に**ファイル**、省略記号ボタン (**.**) ボタンをクリックします。  
  
    3.  **ポリシーの選択** ダイアログ ボックスで、ベスト プラクティス ポリシーを格納している次のフォルダーを参照します。  
  
         **ある C:\Program Files (x86) \Microsoft SQL server \110\tools\policies\databaseengine\1033**  
  
        > [!NOTE]  
        >  ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。  
  
    4.  評価、およびをクリックする 1 つまたは複数の .xml ポリシー ファイルを選択**開く**です。  
  
         選択したファイルの一覧に表示されます、**ファイル**ボックス。  
  
    5.  **ソースの選択**ダイアログ ボックスで、をクリックして**OK**です。  
  
    6.  場合、**ポリシーを読み込んでいます** ダイアログ ボックスが表示されたら、をクリックして**閉じる**です。  
  
     選択したポリシーは次の一覧に表示されます、**ポリシーの選択**ページ。 ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。  
  
5.  をクリックして**評価**ポリシーを評価します。  
  
     **結果**テーブルの場合は、各ポリシーの結果。 赤い "x" アイコンは、ポリシーに準拠していないことを示しています。  
  
6.  一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。 このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。 チェック ボックスを選択した場合、**適用**ボタンができるようになります。 クリックすると、**適用**、非対応の設定は、対象インスタンスに自動的に更新されます。  
  
    > [!CAUTION]  
    >  ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。 1 つ以上のチェック ボックスを選択すると、クリックすることをお勧め**スクリプト**、出力場所を選択して、基になるを確認するようにして[!INCLUDE[tsql](../includes/tsql-md.md)]コードの変更を適用する前にします。  
  
7.  ポリシーの詳細な結果を表示するでのポリシーをクリックして、**結果**テーブル。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [登録済みサーバーを使用した要求時評価の実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  