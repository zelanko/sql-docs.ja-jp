---
title: SQL Server Data Tools のカスタマー エクスペリエンス向上プログラム | Microsoft Docs
ms.custom: ''
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baf3a205-a6bb-4564-8b64-3a0475bb9273
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 58e671eb7e69bbc0487065342b141a5c5bfb1e9a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="customer-experience-improvement-program-for-sql-server-data-tools"></a>SQL Server Data Tools のカスタマー エクスペリエンス向上プログラム
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Microsoft がカスタマー エクスペリエンス向上プログラム (CEIP) により、どのようにしてソフトウェアを改善する方法を特定しているかについて説明します。  有効または無効にするツールはいつでも構成することができます。  
  
> [!NOTE]  
>  Microsoft SQL Server 2016 リリースと、その他の製品およびサービスのユーザー データの収集および使用方法については、この [Microsoft のプライバシーに関する声明](https://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx)を参照してください。  
  
## <a name="opting-in-and-out-of-ceip-for-sql-server-data-tools"></a>SQL Server Data Tools の CEIP を有効または無効にする  
 カスタマー エクスペリエンス向上プログラムは、Microsoft が時間の経過と共に製品を向上させるために記述されたプログラムです。 このプログラムは、コンピューターで実行しているユーザーのタスクを中断することなく、コンピューターのハードウェアおよびユーザーによる製品の利用状況を収集します。 収集される情報は、Microsoft がどの機能を改善するかを特定するために役立ちます。 このドキュメントでは、Visual Studio 2017、Visual Studio 2015 および Visual Studio 2013 で SQL Server Data Tools (SSDT) の CEIP を有効または無効にする方法について説明します。  

### <a name="choice-and-control-over--ceip-and-sql-server-data-tools-for-visual-studio-2017"></a>Visual Studio 2017 の CEIP と SQL Server Data Tools の選択および制御  
 Visual Studio 2017 の SSDT は、SQL Server 2017 に付属するデータ モデリング ツールです。 Visual Studio 2017 に組み込まれている CEIP オプションが使用されます。 Visual Studio 2017 の CEIP を通じてフィードバックを送信する方法の詳細は、[Visual Studio のヘルプ ドキュメント](https://www.visualstudio.com/en-us/docs/work/connect/give-feedback)で確認できます。  
  
 プレビュー版の SQL Server 2017 では、CEIP が既定で有効になっています。 次の手順で、無効にし、再度有効に戻すことができます。  
  
 **Visual Studio の場合 (全言語がインストールされた Visual Studio 2017 に適用されます)**  
  
 既に Visual Studio が含まれているコンピューターに SSDT セットアップを実行する場合は、SQL Server および Business Intelligence プロジェクト テンプレートのみが追加されます。 このシナリオでは、Visual Studio で提供されるカスタマー フィードバックのオプションを使用して CEIP を有効または無効にできます。  
  
1.  Visual Studio を起動します。  
  
2.  [ヘルプ] メニューから、 **[フィードバックの送信]** > **[設定]**を選択します。  
  
3.  CEIP をオフにするには、 **[いいえ、協力しません]**をクリックし、 **[OK]**をクリックします。  
  
     CEIP をオンにするには、 **[はい、協力します]**をクリックし、 **[OK]**をクリックします。  
  

  
 **レジストリ ベースのポリシーまたはグループ ポリシーを使用する**  
  
 Visual Studio 2017 がないコンピューターに SSDT セットアップを実行すると、Visual Studio Shell のみがインストールされます。 このシェルは、カスタマー フィードバックのオプションを提供していません。 この場合、CEIP を構成するための唯一のオプションがレジストリの更新です。  
  
 企業のお客様の場合、SQL Server 2017 のレジストリ ベースのポリシーを設定することにより、有効または無効にするグループ ポリシーが構成されている場合があります。  
  
 これに関連するレジストリ キーと設定は以下のとおりです。  
  
 キー = HKEY_CURRENT_USER\Software\Microsoft\VSCommon\15.0\SQM  
  
 レジストリ エントリ名 = OptIn  
  
 エントリのデータ型 DWORD :  
  
-   0 は無効  
  
-   1 は有効  
  
> [!CAUTION]  
>  レジストリの編集を誤ると、システムに深刻な悪影響を及ぼす可能性があります。 レジストリを変更する前に、コンピューター上のすべての重要なデータをバックアップしておくことをお勧めします。 手動での変更の適用後に問題が発生した場合は、[前回正常起動時の構成] スタートアップ オプションを使うこともできます。  
  
 CEIP によって収集、処理、および転送される情報の詳細については、「 [Microsoft カスタマー エクスペリエンス向上プログラムのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkId=52143)」を参照してください。  
 
### <a name="choice-and-control-over--ceip-and-sql-server-data-tools-for-visual-studio-2015"></a>Visual Studio 2015 の CEIP と SQL Server Data Tools の選択および制御  
 Visual Studio 2015 の SSDT は、SQL Server 2016 に付属するデータ モデリング ツールです。 Visual Studio 2015 に組み込まれている CEIP オプションが使用されます。 Visual Studio 2015 の CEIP を通じてフィードバックを送信する方法の詳細は、 [Visual Studio のヘルプ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=517102)で確認できます。  
  
 プレビュー版の SQL Server 2016 では、CEIP が既定で有効になっています。 次の手順で、無効にし、再度有効に戻すことができます。  
  
 **Visual Studio の場合 (全言語がインストールされた Visual Studio 2015 に適用されます)**  
  
 既に Visual Studio が含まれているコンピューターに SSDT セットアップを実行する場合は、SQL Server および Business Intelligence プロジェクト テンプレートのみが追加されます。 このシナリオでは、Visual Studio で提供されるカスタマー フィードバックのオプションを使用して CEIP を有効または無効にできます。  
  
1.  Visual Studio を起動します。  
  
2.  [ヘルプ] メニューから、 **[フィードバックの送信]** > **[設定]**を選択します。  
  
3.  CEIP をオフにするには、 **[いいえ、協力しません]**をクリックし、 **[OK]**をクリックします。  
  
     CEIP をオンにするには、 **[はい、協力します]**をクリックし、 **[OK]**をクリックします。  
  

  
 **レジストリ ベースのポリシーまたはグループ ポリシーを使用する**  
  
 Visual Studio 2015 がないコンピューターに SSDT セットアップを実行すると、Visual Studio Shell のみがインストールされます。 このシェルは、カスタマー フィードバックのオプションを提供していません。 この場合、CEIP を構成するための唯一のオプションがレジストリの更新です。  
  
 企業のお客様の場合、SQL Server 2016 のレジストリ ベースのポリシーを設定することにより、有効または無効にするグループ ポリシーが構成されている場合があります。  
  
 これに関連するレジストリ キーと設定は以下のとおりです。  
  
 キー = HKEY_CURRENT_USER\Software\Microsoft\VSCommon\14.0\SQM  
  
 レジストリ エントリ名 = OptIn  
  
 エントリのデータ型 DWORD :  
  
-   0 は無効  
  
-   1 は有効  
  
> [!CAUTION]  
>  レジストリの編集を誤ると、システムに深刻な悪影響を及ぼす可能性があります。 レジストリを変更する前に、コンピューター上のすべての重要なデータをバックアップしておくことをお勧めします。 手動での変更の適用後に問題が発生した場合は、[前回正常起動時の構成] スタートアップ オプションを使うこともできます。  
  
 CEIP によって収集、処理、および転送される情報の詳細については、「 [Microsoft カスタマー エクスペリエンス向上プログラムのプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkId=52143)」を参照してください。  
  
### <a name="choice-and-control-for-ceip-and-sql-server-data-tools---bi-ssdt-bi"></a>CEIP および SQL Server Data Tools - BI (SSDT BI) の選択および制御  
 SSDT-BI を使用している場合、インストール中に CEIP に協力するかどうかを選択できます。 SSDT-BI の CEIP の構成は、後でクライアント ツールまたはレジストリ設定の編集により変更することができます。  
  
 **Visual Studio 2013 の SSDT および SSDT-BI の場合**  
  
1.  ツールを起動し、Analysis Services または Integration Services の新規または既存プロジェクトを開きます。  
  
2.  [ヘルプ] メニューから **[Microsoft SQL Server カスタマー フィードバックのオプション]**を選択します。  
  
3.  CEIP を無効にするには、 **[参加しない]**をクリックします。  
  
     CEIP を有効にするには、 **[参加する (推奨)]**をクリックします。  
  
4.  **[OK]** をクリックします。  
  
 **レジストリ ベースのポリシーまたはグループ ポリシーを使用する**  
  
 企業のお客様の場合、SQL Server 2014 のレジストリ ベースのポリシーを設定することにより、有効または無効にするグループ ポリシーが構成されている場合があります。  
  
 これに関連するレジストリ キーと設定は以下のとおりです。  
  
 キー = HKEY_CURRENT_USER\Software\Microsoft\Microsoft SQL Server\120  
  
 レジストリ エントリ名 = CustomerFeedback  
  
 エントリのデータ型 DWORD :  
  
-   0 は無効  
  
-   1 は有効  
  
  
