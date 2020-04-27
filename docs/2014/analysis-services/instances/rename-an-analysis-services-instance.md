---
title: Analysis Services インスタンスの名前を変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3ef94fc86c78e896eab03bffb318b58e4b328245
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079618"
---
# <a name="rename-an-analysis-services-instance"></a>Analysis Services インスタンスの名前変更
  の既存のインスタンスの名前を[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]変更するには、[**インスタンス名の変更**] ダイアログボックスを使用します。  
  
> [!IMPORTANT]  
>  インスタンスの名前を変更しているとき、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool が高度な特権で実行され、インスタンスに関連付けられている Windows サービス名、セキュリティ アカウント、およびレジストリ エントリが更新されます。 これらのアクションを確実に実行するため、このツールは必ずローカルのシステム管理者として実行してください。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool では、元のインスタンスのために作成されたプログラム フォルダーは変更されません。 変更後のインスタンス名に合わせてプログラムのフォルダー名を変更することは避けてください。 プログラム フォルダーの名前を変更すると、セットアップ プログラムによるインストールの修復やアンインストールに支障が生じる場合があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool のクラスター環境での使用はサポートされていません。  
  
### <a name="to-rename-an-instance-of-analysis-services"></a>Analysis Services のインスタンス名を変更するには  
  
1.  C:\Program asinstancerename SQL Server\110\tools\binn\managementstudio から**インスタンス名の変更**ツールを起動し**ます。**  
  
2.  **[インスタンス名の変更]** ダイアログ ボックスの **[名前を変更するインスタンス]** 一覧で、名前を変更するインスタンスを選択します。  
  
3.  **[新しいインスタンス名]** ボックスに、インスタンスの新しい名前を入力します。  
  
4.  ユーザー名とパスワードが正しいことを確認して、 **[名前の変更]** をクリックします。  
  
     名前の変更には、Analysis Services インスタンスの停止と再起動が伴います。  
  
### <a name="post-rename-checklist"></a>名前変更後のチェック リスト  
  
1.  名前変更後のインスタンス上で実行されているデータベースに再度アクセスするためには、Excel などのクライアント アプリケーションからデータ接続を手動で更新する必要があります。 また、Reporting Services の共有データ ソース、Excel ODC ファイル、BI Semantic Model 接続ファイルなど、名前の変更されたインスタンスを参照している可能性のある定義済みの接続をすべてチェックしてください。 詳細については、「 [Analysis Services への接続](connect-to-analysis-services.md)」を参照してください。  
  
2.  データベースのバックアップや同期、処理などに普段使用している PowerShell スクリプトまたは AMO スクリプトを更新します。  
  
3.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用する [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]プロジェクトのプロパティを更新します。 テーブル モードのサーバー インスタンスの場合は、model.bim ファイルの [ワークスペース サーバー] プロパティと、プロジェクトの [サーバー] プロパティを必ず更新してください。  
  
4.  サービス アカウントの指定方法によっては、データへのアクセス権をサービスに付与するデータベース ログインまたはファイル権限を更新する必要があります (サービス アカウントを使用してデータを処理する場合や、別のサーバー上のリンク オブジェクトにアクセスする場合など)。  
  
     仮想アカウントを使用してサービスを準備した場合は、データベース ログインまたはファイル権限を更新する必要があります。 仮想アカウントはインスタンス名に依存するため、インスタンスの名前を変更した場合、同時に仮想アカウントも更新されます。 つまり、変更前のインスタンス用に作成したログインや権限はすべて無効になります。  
  
     具体的な例を次に示します。 既定の仮想アカウントを使用して "表形式" という名前のインスタンスとしてテーブルモードサーバーをインストールしたとします。その結果、次のように構成されます。  
  
    1.  インスタンス名 = \<サーバー> \ 表形式  
  
    2.  サービス名 = MSOLAP$TABULAR  
  
    3.  仮想アカウント = NT Service\ MSOLAP$TABULAR  
  
     ここで、インスタンスの名前を "TAB2" に変更したとします。 名前を変更したことで、必要な構成も次のように変わります。  
  
    1.  インスタンス名 = \<サーバー> \ タブ2  
  
    2.  サービス名 = MSOLAP$TAB2  
  
    3.  仮想アカウント = NT Service\ MSOLAP$TAB2  
  
     ご覧のとおり、以前に "NT サービス \ MSOLAP $ 表形式" に許可されていたデータベースおよびファイルのアクセス許可は無効になりました。 サービスによって実行されるタスクと操作が以前と同じように実行されるようにするには、新しいデータベースとファイルのアクセス許可を "NT Service \ MSOLAP $ TAB2" に付与する必要があります。  
  
  
