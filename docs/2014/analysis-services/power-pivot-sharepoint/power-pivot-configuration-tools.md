---
title: PowerPivot 構成ツール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f934c51d-01fe-4e67-971d-cd87d7d7ee51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 299b40b92b3d2f8c5559a5e10e511f80ab5a5bc9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175661"
---
# <a name="powerpivot-configuration-tools"></a>PowerPivot Configuration Tools
  PowerPivot 構成ツールを使用したの[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]構成、修復、または削除を行います。

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードでは、SharePoint 2010 用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールと SharePoint 2013 用 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールがインストールされます。 このトピックでは、2 つのツールの一般的な用途と相違点について説明します。

 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 2010

 **このトピックの内容**

-   [構成ツールを使用するための要件](#bkmk_requirements)

-   [構成ツールの 2 つのバージョン](#bkmk_twoversions)

-   [PowerPivot 構成ツールの使用の概要](#bkmk_overview)

-   [PowerPivot 構成ツールの起動](#bmkm_start_tool)

##  <a name="requirements-for-using-the-configuration-tools"></a><a name="bkmk_requirements"></a>構成ツールを使用するための要件

-   ファーム管理者である必要があります。

-   Analysis Services インスタンスでサーバー管理者である必要があります (SharePoint 2010 のみ)。

-   ファームの構成データベースに db_owner する必要があります。

-   構成ツールを使用するための TCP/IP ポートの要件はないため、構成ツールに対応するようファイアウォールを構成する必要はありません。 構成ツールを使用するには、Web アプリケーションおよび共有サービスを SharePoint プラットフォームの一部として使用できることが必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー用にファイアウォールを構成することが必要な場合があります。 詳細については、「 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご参照ください。

##  <a name="two-versions-of-the-configuration-tool"></a><a name="bkmk_twoversions"></a>2つのバージョンの構成ツール
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップ ウィザードでは、SharePoint 2010 用 PowerPivot 構成ツールと SharePoint 2013 用 PowerPivot 構成ツールがインストールされます。

 このツールは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] または [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]インスタンスでのみ使用できます。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] インストールでツールを使用しないでください。

|名前|サポートされている SharePoint のバージョン|詳細な構成|
|----------|-------------------------------------|----------------------------|
|PowerPivot for SharePoint 2013 の構成|SharePoint 2013|[PowerPivot for SharePoint 2013 &#40;PowerPivot 構成ツールの構成または修復&#41;](configure-or-repair-power-pivot-for-sharepoint-2013.md)|
|PowerPivot 構成ツール|SharePoint 2010 と SharePoint 2010 の組み合わせ|[PowerPivot for SharePoint 2010 &#40;PowerPivot 構成ツールの構成または修復&#41;](../configure-repair-powerpivot-sharepoint-2010.md)|

###  <a name="how-the-two-configuration-tools-are-different"></a><a name="bkmk_sum_differences_betweentools"></a>2つの構成ツールの違い
 2 つのバージョンの構成ツールは似ていますが、実行する構成手順に違いがあります。 この違いは、SharePoint 2010 と SharePoint 2013 の間の変更と、PowerPivot for SharePoint の SQL Server 2012 SP1 バージョンとそれ以前のバージョンとのアーキテクチャの違いに起因します。

 次の表では、 **PowerPivot for SharePoint 2013 構成** ツールの新機能および変更された機能について説明します。 また、PowerPivot for SharePoint 2013 構成ツールに含まれていない **PowerPivot 構成ツール** の機能についても説明します。 表の行は、構成ツールのタブと同じ順序で並んでます。

|PowerPivot for SharePoint 2013 の構成|PowerPivot 構成ツール|
|--------------------------------------------------|-----------------------------------|
|メイン ページには、 **[Excel Services 用 PowerPivot サーバー]** という新しいオプションがあります。 このオプションでは、SharePoint ファームの外部で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行できる新しいアーキテクチャがサポートされます。 SharePoint モードで実行されている 1 つ以上の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーを使用するように Excel Services を構成します。<br /><br /> ![新しい構成ツールでの PowerPivot サーバー](../media/as-powerpivot-configtool-differences-new-mainpage.gif "新しい構成ツールでの PowerPivot サーバー")||
||2010ツールには、の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ローカルインスタンスを構成するためのページ**登録 SQL Server Analysis Services (PowerPivot) がローカルサーバーに**含まれています。 このページは 2013 ツールにはありません。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のローカル インスタンスが存在しないためです。<br /><br /> ![古い構成ツールでの AS サービス アカウント](../media/as-powerpivot-configtool-differences-old-register-as-localserver.gif "古い構成ツールでの AS サービス アカウント")|
||**[PowerPivot サービス アプリケーションの作成]** ページには、 **[ブックをアップグレードして、データ更新を有効にします]** という追加のオプションがあります。 このオプションは、2013 ツールでは使用できません。<br /><br /> ![古い構成ツールでのブックのアップグレード](../media/as-powerpivot-configtool-differences-old-uprgadeworkbooks.gif "古い構成ツールでのブックのアップグレード")|
|2013 ツールには、 **[PowerPivot サーバーの構成]** という新しいページがあります。 このページでは、SharePoint ファームの外部で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を実行できる新しいアーキテクチャがサポートされます。 既定では、メイン ページの **[Excel Services 用 PowerPivot サーバー]** ボックスに入力したサーバー名も **[PowerPivot サーバーの構成]** に表示されます。<br /><br /> ![新しい構成ツールでの PowerPivot サーバーの登録](../media/as-powerpivot-configtool-differences-new-powerpivot-servers.gif "新しい構成ツールでの PowerPivot サーバーの登録")||
|2013 ツールには、 **[Excel Services Usage Tracker として PowerPivot アドインを登録します]** という新しいページがあります。 SharePoint 2010 の Excel Services では、PowerPivot の使用状況データを追跡しません。||
||2010 ツールには、SharePoint 2010 の Excel Services で PowerPivot モデルを読み込むことができるように MSOLAP を登録する **[MSOLAP.5 を信頼できるプロバイダーとして追加]** ページがあります。 このページは、2013 ツールにはありません。 SharePoint 2013 の Excel Services では、モデルの読み込みに MSOLAP プロバイダーを使用しません。|

##  <a name="overview-of-using-a-powerpivot-configuration-tool"></a><a name="bkmk_overview"></a>PowerPivot 構成ツールの使用の概要
 どちらの PowerPivot 構成ツールも起動すると、既存のインストールが評価され、適用可能な操作が確認されます。 新しいインストールでは、構成タスクのみが利用可能です。 サーバーを構成した後は、削除タスクが表示されます。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] インスタンスで起動した場合は、利用可能なタスクの一覧でアップグレードも有効になります。

 サーバーの全体管理または Windows PowerShell に慣れていない場合は、代わりに構成ツールを実行して、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストールを完了します。

 また、このツールを使用すると、ファームが構成済みか、または必要な機能が不足しているかを検出できます。 SharePoint プログラム ファイルがインストールされている一方でファームが構成されていない場合、このツールは、ファームと [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストールの両方を構成するためのアクションを提供します。

 **[スクリプト]** タブを確認すると、Windows PowerShell を使用して、PowerPivot および SharePoint を構成する方法を学習し、理解できます。 詳細については、「

-   [Windows PowerShell を使用した PowerPivot の構成](power-pivot-configuration-using-windows-powershell.md)

-   [PowerShell リファレンス (PowerPivot for SharePoint)](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)

> [!NOTE]
>  このツールでは、Reporting Services は構成できません。 Reporting Services を SharePoint 環境に追加する場合は、Reporting Services を個別にインストールし、構成する必要があります。 詳細については、「
> 
>  -   [Sharepoint 2013 用 Reporting Services Sharepoint モードをインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)します。
> -   [Sharepoint 2010 用 Reporting Services Sharepoint モードをインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)します。

##  <a name="start-one-of-the-powerpivot-configuration-tools"></a><a name="bmkm_start_tool"></a>PowerPivot 構成ツールの1つを開始します。

1.  **スタート**画面で、「」と入力します。`powerpivot`

     **スタート**画面`powerpivot`で、[**スタート**] ボタンをクリックし、[**すべてのプログラム** [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、[]、[**構成ツール**] の順にクリックして、次のいずれかをクリックします。

    -   **PowerPivot 構成ツール**

    -   **OR**

    -   **PowerPivot for SharePoint 2013 の構成**

     ![2 つの PowerPivot 構成ツール](../media/as-powerpivot-configtools-bothicons.gif "2 つの PowerPivot 構成ツール")

     **注:** このツールは、ローカル サーバーに [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] がインストールされている場合にのみ使用できます。

2.  構成ツールが起動されると、インストールのステータスがチェックされ、インストールに有効なタスクが提供されます。

3.  インストールの現在の状態に応じて、次の 1 つ以上のタスクを実行できます。

    1.  [ **PowerPivot for SharePoint の構成または修復**] をクリックして、インストール後のタスクを完了するか、インストールを修復します。

    2.  **[機能、サービス、アプリケーション、およびソリューションの削除]** をクリックして、ファームから機能とソリューションを削除します。

    3.  **[機能、サービス、アプリケーション、およびソリューションのアップグレード]** をクリックして、以前のバージョンの [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]を使用してインストールされた機能とソリューションをアップグレードします。

     たとえば、次の図は PowerPivot for SharePoint 2013 構成ツールの最初のページを示しています。

     ![PowerPivot for SharePoint 2013 構成ツール](../media/ssas-powerpivot-configtool-4-sharepoint2013-choosemode.gif "PowerPivot for SharePoint 2013 構成ツール")

 各タスクは、サーバーの構成のいくつかの側面に対応する個々のアクションで構成されます。 たとえば、構成タスクには、ソリューションの配置、PowerPivot サービス アプリケーションの作成、機能のアクティブ化、データ更新の構成などのアクションが含まれます。 アクションの一覧は、インストールの現在の状態によって異なります。 必要でないアクションは、タスクの一覧から除外されます。

 [実行] をクリックすると、すべてのアクションがバッチ モードで処理されます。 各アクションはタスクの一覧で別個のアイテムとして表示されますが、タスクに含まれるすべてのアクションが一度に処理されます。 検証チェックに合格したアクションのみが処理されます。 検証チェックに合格するために、いくつかの入力値を追加または変更することが必要になる場合があります。

## <a name="related-content"></a>関連コンテンツ
 [Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) ファームにある既存のインストールをアップグレードするためのワークフローについて説明します。

 [Uninstall PowerPivot for SharePoint](../../sql-server/install/uninstall-power-pivot-for-sharepoint.md) PowerPivot for SharePoint サービス、ソリューション、およびアプリケーション ページをファームから削除するためのワークフローについて説明します。

 [Windows PowerShell を使用した PowerPivot の構成](power-pivot-configuration-using-windows-powershell.md)

 [サーバーの全体管理での PowerPivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)


