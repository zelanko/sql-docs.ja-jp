---
title: バッチ処理 (Analysis Services) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d2f72dd0c7b380391a7b500d494d5aac83c4c6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="batch-processing-analysis-services"></a>バッチ処理 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、Batch コマンドを使用して、1 つの要求で複数の処理コマンドをサーバーに送信することができます。 バッチ処理では、どのオブジェクトがどの順序で処理されるのかを制御できます。 また、バッチは、一連のスタンドアロン ジョブとして実行するか、1 つのプロセスが失敗したときにバッチ全体をロールバックするトランザクションとして実行することもできます。  
  
 バッチ処理では、変更をコミットするのに必要な時間をまとめることで短縮し、データの可用性を最大にします。 ディメンションを完全に処理すると、そのディメンションを使用するパーティションには未処理のマークが付きます。 その結果、未処理のパーティションを含むキューブは参照できなくなります。 この問題は、バッチ処理ジョブを使用し、影響を受けるパーティションと共にディメンションを処理することで対処できます。 バッチ処理ジョブをトランザクションとして実行すると、すべての処理が完了するまで、そのトランザクションに含まれるすべてのオブジェクトをクエリ用に使用できます。 トランザクションが変更をコミットするときに、影響を受けるオブジェクトはロックされるため、オブジェクトは一時的に使用できなくなります。ただし、変更をコミットするために必要な全体の時間は、オブジェクトを個々に処理した場合よりも短縮されます。  
  
 このトピックでは、ディメンションおよびパーティションを完全に処理する手順を示します。 バッチ処理には、増分処理などの他の処理オプションを含めることもできます。 この手順を正しく実行するためには、少なくとも 2 つのディメンションと 1 つのパーティションを含む既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを使用する必要があります。  
  
 このトピックのセクションは次のとおりです。  
  
 [SQL Server データ ツールでのバッチ処理](#bkmk_ssdt)  
  
 [Management Studio での XMLA を使用したバッチ処理](#bkmk_xmla)  
  
##  <a name="bkmk_ssdt"></a> SQL Server データ ツールでのバッチ処理  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]でオブジェクトを処理するには、そのオブジェクトを含んでいるプロジェクトを配置する必要があります。 詳細については、「[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を開きます。  
  
2.  配置されているプロジェクトを開きます。  
  
3.  ソリューション エクスプローラーで、配置されたプロジェクトの **[ディメンション]** フォルダーを展開します。  
  
4.  Ctrl キーを押しながら、 **[ディメンション]** フォルダーに一覧表示されている各ディメンションをクリックします。  
  
5.  選択したディメンションを右クリックし、 **[処理]** をクリックします。  
  
6.  Ctrl キーを押しながら、 **[オブジェクト一覧]** に表示されている各ディメンションをクリックします。  
  
7.  選択したディメンションを右クリックし、 **[完全処理]** を選択します。  
  
8.  バッチ処理ジョブをカスタマイズするには、 **[設定の変更]** をクリックします。  
  
9. **[処理オプション]** で、以下の設定を行います。  
  
    -   **[処理順序]** を **[シーケンシャル]** に、 **[トランザクション モード]** を **[1 つのトランザクション]** に設定します。  
  
    -   **[書き戻しテーブル オプション]** を **[既存のデータを使用する]** に設定します。  
  
    -   **[影響を受けたオブジェクト]** の **[影響を受けたオブジェクトを処理する]** チェック ボックスをオンにします。  
  
10. **[ディメンション キーのエラー]** タブをクリックします。**[既定のエラー構成を使用する]** が選択されていることを確認します。  
  
11. **[OK]** をクリックし、 **[設定の変更]** 画面を閉じます。  
  
12. **[ディメンションの処理]** 画面で **[実行]** をクリックし、処理ジョブを開始します。  
  
13. **[状態]** ボックスに **"処理が成功しました"** と表示されたら、 **[閉じる]** をクリックします。  
  
14. **[ディメンションの処理]** 画面で **[閉じる]** をクリックします。  
  
##  <a name="bkmk_xmla"></a> Management Studio での XMLA を使用したバッチ処理  
 バッチ処理を実行する XMLA スクリプトを作成することができます。 まず、各オブジェクトに対して、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で XMLA スクリプトを生成し、次にそれらを対話形式で、またはスケジュールされているタスク内で実行する単一の XMLA クエリに統合します。  
  
 段階を追った手順については、「 **SQL Server エージェントで SSAS 管理タスクのスケジュール設定を行う** 」の [Schedule SSAS Adm」のistrative Tasks with SQL Server Agent](../../analysis-services/instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
