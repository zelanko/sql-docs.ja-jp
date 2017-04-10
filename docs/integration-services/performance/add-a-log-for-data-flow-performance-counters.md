---
title: "データ フロー パフォーマンス カウンターのログを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パフォーマンス カウンター [Integration Services]"
  - "カウンター [Integration Services]"
  - "ログ [Integration Services]、データ フロー カウンター"
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# データ フロー パフォーマンス カウンターのログを追加する
  この手順では、データ フロー エンジンによって提供されるパフォーマンス カウンターのログを追加する方法について説明します。  
  
> [!NOTE]  
>  [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] を実行するコンピューターに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールした後、コンピューターを [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] にアップグレードすると、アップグレード プロセスにより [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターがコンピューターから削除されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターをコンピューターに復元するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップを修復モードで実行してください。  
  
### パフォーマンス カウンターのログを追加するには  
  
1.  **[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]** をクリックします。 カテゴリ表示を使用している場合は、**[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。  
  
2.  **[パフォーマンス]** をクリックします。  
  
3.  **[パフォーマンス]** ダイアログ ボックスで、**[パフォーマンス ログと警告]** を展開して、**[カウンター ログ]** を右クリックし、**[新しいログの設定]** をクリックします。 ログの名前を入力します。 たとえば、「**MyLog**」のように入力します。  
  
4.  **[OK]**をクリックします。  
  
5.  **[MyLog]** ダイアログ ボックスで、**[カウンターの追加]** をクリックします。  
  
6.  ローカル コンピューターのパフォーマンス カウンターを記録するには、**[ローカル コンピューターのカウンターを使う]** をオンにします。指定したコンピューターのパフォーマンス カウンターを記録するには、**[次のコンピューターからカウンターを選ぶ]** をオンにし、一覧からコンピューターを選択します。  
  
7.  **[カウンターの追加]** ダイアログ ボックスで、**[パフォーマンス オブジェクト]** 一覧の **[SQL Server:SSIS Pipeline]** をクリックします。  
  
8.  パフォーマンス カウンターを選択するには、次のいずれかの操作を行います。  
  
    -   すべてのパフォーマンス カウンターを記録する場合は、**[すべてのカウンター]** をクリックします。  
  
    -   **[一覧からカウンターを選ぶ]** をオンにし、使用するパフォーマンス カウンターを選択します。  
  
9. **[追加]**をクリックします。  
  
10. **[閉じる]**をクリックします。  
  
11. **[MyLog]** ダイアログ ボックスの **[カウンター]** 一覧で、ログ パフォーマンス カウンターの一覧を確認します。  
  
12. カウンターを追加するには、手順 5. ～ 10. を繰り返します。  
  
13. **[OK]**をクリックします。  
  
    > [!NOTE]  
    >  [パフォーマンス ログと警告] サービスは、Administrators グループのメンバーであるローカル アカウントまたはドメイン アカウントを使用して起動する必要があります。  
  
## 参照  
 [パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)   
 [[ログ イベント] ウィンドウでログ エントリを表示する](../Topic/View%20Log%20Entries%20in%20the%20Log%20Events%20Window.md)  
  
  