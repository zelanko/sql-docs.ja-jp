---
title: ネイティブ モード レポート サーバーに接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.rsconfigtool.connectiondialog.F1
helpviewer_keywords:
- report servers [Reporting Services], configuring
ms.assetid: 8b9ea8d3-827c-4011-9e02-be2eac3bb364
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 703e25f513fa8482d62d8c454aca1dbe0edea92a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084027"
---
# <a name="connect-to-a-native-mode-report-server"></a>ネイティブ モードのレポート サーバーへの接続
  このダイアログ ボックスを使用して、ローカルまたはリモートに接続[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバー インスタンス。 以前のバージョンへの接続にこのツールを使用することはできません[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバー。 一度に接続できるインスタンスは 1 つだけです。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager の構成および管理するのには使用されません[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。 SharePoint モードでレポート サーバーを構成するには、SharePoint サーバーの全体管理と PowerShell スクリプトを使用します。 詳細については、次を参照してください[Install Reporting Services SharePoint Mode for SharePoint 2010。](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
> [!TIP]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成マネージャー (RSConfigTool.exe) は、"highestAvailable"の特権レベルと共にインストールします。 この動作は仕様による結果です。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI API と通信する必要があります。 一部の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]WMI 通信には、高いレベルまたは管理者の特権が必要です。  
  
-   ローカル レポート サーバー インスタンスに接続するには、既定値を使用して **[接続]** をクリックします。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーにより、ローカル サーバー名が提供され、既定のインスタンスが検出されます。 ほとんどの場合、値を変更せずに **[接続]** をクリックできます。 複数のインスタンスがインストールされている場合は、使用するインスタンスを選択する必要があります。  
  
-   リモート レポート サーバー インスタンスに接続するには、サーバー名を入力して **[検索]** をクリックします。次に、インスタンスを選択して **[接続]** をクリックします。  
  
 このダイアログ ボックスを開くを起動、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager です。 このダイアログ ボックスは、ツールを起動すると直ちに表示されます。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[サーバー名]**  
 いるコンピューターのネットワーク名を入力[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]がインストールされています。 プレフィックスやスラッシュを含めずに、コンピューター名だけを入力してください。  
  
 **検索**  
 **[サーバー名]** で指定したコンピューターを検索します。  
  
 **レポート サーバー インスタンス**  
 複数のレポート サーバー インスタンスをインストールしている場合は、接続先のインスタンスを選択します。 選択できるのは有効なインスタンスだけです。 以前のバージョンを実行している場合[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サイド バイ サイド、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、それらのインスタンスが一覧に表示されません。  
  
 **のインスタンスに接続するときには、**  
 指定したサーバーおよびインスタンスに接続します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  