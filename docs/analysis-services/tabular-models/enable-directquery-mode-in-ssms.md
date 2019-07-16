---
title: SSMS で Analysis Services の DirectQuery モードで有効にする |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 27e704e6274910e2c9e3f77fe235e02918d95425
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207657"
---
# <a name="enable-directquery-mode-in-ssms"></a>SSMS での DirectQuery モードの有効化
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  既にデプロイされている表形式モデルのデータ アクセス プロパティは、DirectQuery モードを有効にすることで変更できます。このときクエリは、メモリ内にあるキャッシュ データではく、バックエンドのリレーショナル データ ソースに対して実行されます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、DirectQuery の構成はモデルの互換性レベルにより異なります。 すべての互換性レベルで動作する手順を下記で説明します。  
  
 この記事では、作成、互換性レベル 1200 以上で DirectQuery へのアクセスを有効にして、接続文字列を更新する必要があるだけのメモリ内表形式モデルの検証が前提としています。 これよりも低い互換性レベルから開始する場合は、最初に手動でアップグレードする必要があります。 手順については、「 [Analysis Services のアップグレード](../../database-engine/install-windows/upgrade-analysis-services.md) 」をご覧ください。  
  
> [!IMPORTANT]  
>  データ ストレージ モードを切り替えるには、Management Studio ではなく、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の使用をお勧めします。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を使用してモデルを変更すると、サーバーにデプロイされ、モデルとデータベースが同期します。さらに、モデル内のストレージ モードを変更すると、発生した検証エラーを確認できます。 この記事で説明するように [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用すると、検証エラーは報告されません。  
  
## <a name="requirements"></a>必要条件  
 表形式モデルで DirectQuery モードを使用できるようにするには、複数の手順を行います。  
  
-   モデルに DirectQuery モードで検証エラーが発生する機能がないことを確認し、モデルのデータ ストレージ モードをメモリ内から DirectQuery に変更します。  
  
     機能の制限の一覧が記載されて[DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)します。  
  
-   デプロイ済みのデータベースを使用して接続文字列と資格情報を確認し、バックエンドの外部データベースからデータを取得します。 接続は 1 つだけであること、また、設定がクエリの実行に適していることを確認します。  
  
     DirectQuery 用に特化して設計されていない表形式のデータベースには、複数の接続があることがあります。DirectQuery モードで必須となるため、接続を 1 つにする必要があります。  
  
     元々データ処理に使う資格情報が、これでデータにクエリを実行するために使用できます。 DirectQuery 構成の一環として、アカウントを確認し、専用の操作用に別の資格情報を使用する場合はアカウントを変更します。  
  
     DirectQuery モードは、Analysis Services が信頼する委任の唯一のシナリオです。 ソリューションが委任を呼んで、ユーザー固有のクエリの結果を取得する場合は、バックエンド データベースへの接続に使用されているアカウントが、要求によりユーザー ID を委任する必要があります。また、ユーザー ID は、バックエンド データベースを読み取るアクセス許可を所有している必要があります。  
  
-   最後の手順として、DirectQuery モードがクエリを実行して動作することを確認します。  
  
## <a name="step-1-check-the-compatibility-level"></a>手順 1:互換性レベルを確認してください。  
 データ アクセスを定義するプロパティは、互換性レベルで異なります。 準備の段階として、データベースがどの互換性レベルなのか確認してください。  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の場合、表形式モデルのあるインスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]**  >  **[互換性レベル]** の順にクリックします。  
  
     値は、**SQL Server 2016 (1200)** または **SQL Server 2012 SP1 or later (1103)** のどちらかになります。 次に、互換性レベルに対して有効な手順を行います。  
  
 表形式モデルを DirectQuery モードに変更すると、すぐに新しいデータ ストレージ モードが有効になります。  
  
## <a name="step-2a-switch-a-tabular-1200-database-to-directquery-mode"></a>手順 2 a:表形式 1200 データベースを DirectQuery モードに切り替える  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]**  >  **[モデル]**  >  **[既定のモード]** の順にクリックします。  
  
2.  モードを **[DirectQuery]** に設定します。  
  
    |||  
    |-|-|  
    |**有効な値**|**[説明]**|  
    |**DirectQuery**|クエリは、モデルに定義されているデータ ソース接続を使用して、バックエンド リレーショナル データベースに対して実行されます。<br /><br /> モデルへのクエリは、ネイティブ データベース クエリに変換され、データ ソースにリダイレクトします。<br /><br /> モデル セットを DirectQuery モードで処理すると、メタデータのみがコンパイルされ、デプロイされます。 データ自体はモデルの外部にあり、稼動しているデータ ソースのデータベース ファイルに存在します。|  
    |**[インポート]**|クエリは、MDX または DAX の表形式データベースに対して実行されます。<br /><br /> モデル セットをインポート モードで処理すると、データはバックエンド データ ソースから取得され、ディスクに格納されます。 データベースがロードされると、非常に高速のテーブル スキャンやクエリが実行され、データ全体がメモリにコピーされます。<br /><br /> これは表形式モデルの既定のモードで、特定の (非リレーショナル) データ ソースに適応する唯一のモードです。|  
  
## <a name="step-2b-switch-a-tabular-1100-1103-database-to-directquery-mode"></a>手順 2 b:表形式の 1100 から 1103 データベースを DirectQuery モードに切り替える  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]**  >  **[データベース]**  >  **[DirectQueryMode]** の順にクリックします。  
  
2.  モードを **[DirectQuery]** に設定します。  
  
     既定のモードのプロパティは、次のように構成されています。  
  
    |||  
    |-|-|  
    |**有効な値**|**[説明]**|  
    |**InMemory**|クエリは、キャッシュされたメモリ内のデータのみを使用します。|  
    |**InMemoryWithDirectQuery**|クライアントから接続文字列で指定されていない限り、既定ではクエリでキャッシュが使用されます。<br /><br /> これは、パーティションが個別に構成されているハイブリッド モードで、メモリ内または DirectQuery を使用します。|  
    |**DirectQuery**|クエリでは、リレーショナル データ ソースのみ使用します。|  
    |**DirectQueryWithInMemory**|クライアントから接続文字列で特に指定されていない限り、既定ではクエリでリレーショナル データ ソースが使用されます。<br /><br /> これは、パーティションが個別に構成されているハイブリッド モードで、メモリ内または DirectQuery を使用します。|  
  
 **ハイブリッド データ ストレージ**  
  
 メモリ内とディスク ベースのアクセスを組み合わせて使用すると、キャッシュは引き続き使用でき、クエリの実行に使えます。 ハイブリッド モードには、多くのオプションが用意されています。  
  
-   キャッシュとリレーショナル データ ソースの両方が使用可能な場合は、優先される接続方法を設定できますが、最終的には、クライアントが DirectQueryMode 接続文字列プロパティを使用して、使用されるソースを制御します。  
  
-   DirectQuery モードに使用されるプライマリ パーティションが処理されず、常にリレーショナル ソースを参照する方法で、キャッシュにパーティションを構成することができます。 モデル デザインとレポート環境を最適化するために、多くの方法でパーティションを使用できます。 詳細については、次を参照してください。 [DirectQuery モデルでパーティションを定義](../../analysis-services/tabular-models/define-partitions-in-directquery-models-ssas-tabular.md)します。  
  
-   モデルが配置された後、優先される接続方法を変更できます。 たとえば、テストにはハイブリッド モードを使用し、モデルを使用するレポートまたはクエリを完全にテストした後でのみ **DirectQuery のみ** のモードに切り替えることができます。 詳しくは、「 [DirectQuery の優先接続方法の設定または変更](http://msdn.microsoft.com/library/f10d5678-d678-4251-8cce-4e30cfe15751)」をご覧ください。  
  
## <a name="step-3-check-the-connection-properties-on-the-database"></a>手順 3:データベースの接続のプロパティを確認してください。  
 データ ソース接続のセットアップ方法に応じて、DirectQuery を切り替えると、接続のセキュリティ コンテキストを変更することができます。 データ アクセス モードを変更するときに、偽装や接続文字列プロパティをチェックして、バックエンド データベースに接続しているログインが有効であることを確認してください。  
  
 「 **Configure Analysis Services for Kerberos constrained delegation** 」の「 [信頼された委任用に Analysis Services を構成する](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md) 」セクションを確認します。こちらでは、DirectQuery シナリオのユーザー ID の委任について、その経緯を説明しています。  
  
1.  オブジェクト エクスプローラーで、 **[接続]** を展開し、[接続] をダブルクリックして、該当するプロパティを表示します。  
  
     DirectQuery モデルの場合は、データベースに定義されている接続は 1つのみです、また、データ ソースはリレーショナルで、サポートされているデータベース型にする必要があります。 参照してください[サポートされるデータ ソース](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)します。  
  
2.  **[接続文字列]** がサーバー、データベース名、および DirectQuery 操作で使用する認証方法を指定します。 SQL Server 認証を使用している場合は、こちらでデータベース ログインを指定できます。  
  
3.  **[権限借用情報]** は、Windows の認証に使用されます。 DirectQuery モードの表形式モデルで有効なオプションは次のとおりです。  
  
    -   **サービス アカウントの使用**。 Analysis Services サービス アカウントがリレーショナル データベースの読み取りアクセス許可を所有している場合、このオプションを選べます。  
  
    -   **特定のユーザーとパスワードの使用**。 リレーショナル データベースの読み取りアクセス許可を持つ Windows のユーザー アカウントを指定します。  
  
 これらの資格情報は、リレーショナル データ ストアに対するクエリの応答にのみ使用されます。これらはハイブリッド モデルのキャッシュの処理に使用される資格情報と同じではありません。  
  
 モデルをメモリ内でのみ使用する場合は、権限借用を使用できません。 モデルで DirectQuery モードを使用していない限り、 **ImpersonateCurrentUser**設定は無効です。  
  
## <a name="step-4-validate-directquery-access"></a>手順 4:DirectQuery アクセスを検証します。  
  
1.  Management Studio で、SQL Server のリレーショナル データベースに接続しながら、SQL Server Profiler または xEvents を使用して、トレースを開始します。  
  
     Oracle または Teradata を使用している場合は、これらのデータベース プラットフォームのトレース ツールを使用します。  
  
2.  Management Studio で、 `select <some measure> on 0 from model.`など、シンプルな MDX クエリを入力して、実行します。  
  
3.  トレースすると、リレーショナル データベースでクエリが実行された証拠が表示されるはずです。  
  
## <a name="see-also"></a>関連項目  
 [互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [サポートされるデータ ソース](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)   
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   

  
  
