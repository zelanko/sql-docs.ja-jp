---
title: 1つのインスタンスにポリシーをインポートする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 410f3a317a9d3ad2f8cab52d9f57fd4a63c1c36c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62865101"
---
# <a name="import-the-policies-to-a-single-instance"></a>単一インスタンスへのポリシーのインポート
  ここでは、スケジュールするベスト プラクティス ポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の単一インスタンス上のポリシー ベースの管理にインポートします。  
  
## <a name="prerequisites"></a>前提条件  
 この手順は、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンを実行しているサーバー上で実行する必要があります。  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>データベース エンジンのベスト プラクティス ポリシーのインポート  
  
1.  を[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]起動し、に接続し[!INCLUDE[ssDE](../includes/ssde-md.md)]ます。  
  
2.  オブジェクトエクスプローラーで、[**管理**]、[**ポリシー管理**] の順に展開します。  
  
3.  [**ポリシー**] を右クリックし、[**ポリシーのインポート**] をクリックします。  
  
4.  [**インポート**] ダイアログボックスで、[**インポートするファイル**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。  
  
5.  [**検索対象**] ボックスの一覧で、ベストプラクティスポリシーが含まれている次のフォルダーを参照します。  
  
     **C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。  
  
6.  **[ポリシーの選択**] ダイアログボックスで、1つまたは複数のポリシーファイルを選択します。  
  
     隣接していない複数のファイルを選択するには、ファイルをクリックし、Ctrl キーを押しながら他のファイルをそれぞれクリックします。 隣接する複数のファイルを選択するには、最初のファイルをクリックし、Shift キーを押しながら最後のファイルをクリックします。  
  
7.  ファイルの選択が完了したら、[**開く**] をクリックします。  
  
8.  [**インポート**] ダイアログボックスで、[ポリシーの**状態**] ボックスの一覧が [**インポート時にポリシーの状態を保持**する] (既定値) に設定されていることを確認し、[ **OK**] をクリックします。  
  
     ポリシーは、[**ポリシー管理**] の下にある [**ポリシー** ] ノードにインポートされます。 既定では、インポートされたポリシーは "要求時" 評価モードに設定されます。  
  
## <a name="next-steps"></a>次の手順  
 [ポリシーのスケジュール設定](../../2014/tutorials/schedule-the-policies.md)  
  
  
