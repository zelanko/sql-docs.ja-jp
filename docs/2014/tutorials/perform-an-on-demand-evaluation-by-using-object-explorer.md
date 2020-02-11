---
title: オブジェクトエクスプローラー | を使用して要求時評価を実行します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8d2aadd055334c7ee64871c2fdfe5239c9849e90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68210943"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a>オブジェクト エクスプローラーを使用した要求時評価の実行
  ここでは、オブジェクト エクスプローラーを使用して、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] の単一インスタンス上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に対して、ベスト プラクティス ポリシーの要求時評価を実行します。  
  
> [!NOTE]  
>  単一インスタンス上のポリシーの評価は、登録済みサーバーを通じて行うこともできます。 詳細については、「[登録済みサーバーを使用したオンデマンド評価の実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 このレッスンでは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のバージョンを使用します。  
  
> [!NOTE]  
>  を実行[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]しているインスタンスに対してベストプラクティスポリシーの要求時評価を実行するには、「[登録済みサーバーを使用して要求時評価を実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)する」の手順を実行する必要があります。  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a>オブジェクト エクスプローラーを使用して要求時評価を実行するには  
  
1.  を[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]起動し、に接続し[!INCLUDE[ssDE](../includes/ssde-md.md)]ます。  
  
2.  オブジェクトエクスプローラーで、[**管理**]、[**ポリシー管理**] の順に展開し、[**ポリシー**] を右クリックして、[**評価**] をクリックします。  
  
    > [!NOTE]  
    >  既定では、ローカル インスタンスがポリシーのソースとして使用されます。 ベスト プラクティス ポリシーを以前にインポートしている場合は、作成済みのポリシーがあれば、それと共に一覧表示されます。 インポートされたベストプラクティスポリシーを選択し、[**評価**] をクリックします。 ベスト プラクティス ポリシーをインポートしていない場合には、この手順を続行します。  
  
3.  [**ポリシーの評価**] ダイアログボックスの [**ソース**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。  
  
4.  [**ソースの選択**] ダイアログボックスで、評価するポリシーファイルのソースとして [**ファイル**] または [**サーバー** ] を選択できます。 [**サーバー**] をクリックすると、以前にローカルサーバーまたはリモートサーバー上のポリシーベースの管理にインポートされたベストプラクティスポリシーの要求時評価を実行できます。 このチュートリアルでは、[**ファイル**] をクリックし、評価する個々のポリシーファイルを選択します。 そのためには、次の手順に従います。  
  
    1.  [**ファイル**] をクリックします。  
  
    2.  [**ファイル**] の横にある省略記号ボタン ([.**..**]) をクリックします。  
  
    3.  **[ポリシーの選択**] ダイアログボックスで、次のフォルダーに移動します。このフォルダーには、ベストプラクティスポリシーが含まれています。  
  
         **C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
        > [!NOTE]  
        >  ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。  
  
    4.  評価する1つまたは複数の .xml ポリシーファイルを選択し、[**開く**] をクリックします。  
  
         選択したファイルの一覧が [**ファイル**] ボックスに表示されます。  
  
    5.  [**ソースの選択**] ダイアログボックスで、[ **OK**] をクリックします。  
  
    6.  [**ポリシーの読み込み**] ダイアログボックスが表示されたら、[**閉じる**] をクリックします。  
  
     選択したポリシーは、[ポリシーの**選択**] ページに一覧表示されます。 ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。  
  
5.  [**評価**] をクリックしてポリシーを評価します。  
  
     **結果**テーブルには、各ポリシーの結果が一覧表示されます。 赤い "x" アイコンは、ポリシーに準拠していないことを示しています。  
  
6.  一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。 このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。 チェックボックスをオンにすると、[**適用**] ボタンが使用できるようになります。 [**適用**] をクリックすると、準拠していない設定がターゲットインスタンスで自動的に更新されます。  
  
    > [!CAUTION]  
    >  ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。 1つ以上のチェックボックスをオンにした後、[**スクリプト**] をクリックし、出力場所を選択して、変更[!INCLUDE[tsql](../includes/tsql-md.md)]を適用する前に基になるコードを確認できるようにすることをお勧めします。  
  
7.  ポリシーの詳細な結果を表示するには、[**結果**] テーブルでポリシーをクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [登録済みサーバーを使用した要求時評価の実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
