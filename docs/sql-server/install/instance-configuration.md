---
title: インストール ウィザードのヘルプ | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- instance configuration, Setup
helpviewer_keywords:
- Instance Name page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Instance Name page
ms.assetid: 5bf822fc-6dec-4806-a153-e200af28e9a5
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: c5aa429284ae8eec9c47e752b918be7fae723a9d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029123"
---
# <a name="installation-wizard-help"></a>インストール ウィザードのヘルプ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの構成ページの一部について説明します。 

## <a name="instance-configuration"></a>インスタンスの構成
**インストール ウィザードの** [インスタンスの構成] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既定のインスタンスまたは名前付きインスタンスのどちらを作成するのかを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがまだインストールされていない場合は、名前付きインスタンスを指定しない限り、既定のインスタンスが作成されます。  
  
各 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、照合順序などのオプションに固有の設定を持つ異なるサービス セットから構成されます。 ディレクトリ構造、レジストリ構造、およびサービス名には、すべて [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ中に作成されるインスタンス名および特定のインスタンス ID が反映されます。  
  
 インスタンスには、既定のインスタンスと名前付きインスタンスがあります。 既定のインスタンス名は MSSQLSERVER です。 接続時に、クライアントでインスタンス名を指定する必要はありません。 名前付きインスタンスは、ユーザーがセットアップ中に指定します。 先に既定のインスタンスをインストールしなくても、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を名前付きインスタンスとしてインストールできます。 既定のインスタンスにできるのは、バージョンにかかわらず、一度に 1 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストールだけです。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep では、**[インスタンスの構成]** ページで準備済みインスタンスを完了するときにインスタンス名を指定できます。 コンピューター上に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既存のインスタンスがない場合は、完了しようとしている準備済みインスタンスを既存のインスタンスとして構成するように選択できます。  
  
### <a name="multiple-instances"></a>複数のインスタンス  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、1 台のサーバー (1 つのプロセッサ) 上に複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスをインストールできます。ただし、既定のインスタンスにできるのはそのうち 1 つだけです。 その他のインスタンスはすべて、名前付きインスタンスにする必要があります。 コンピューターは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンスを同時に実行でき、それぞれ他のインスタンスとは関係なく動作します。  
  
 詳しくは、「 [Maximum Capacity Specifications for SQL Server](../maximum-capacity-specifications-for-sql-server.md)」をご覧ください。  
  
### <a name="options"></a>オプション  
 フェールオーバー クラスター インスタンスのみ - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターのネットワーク名を指定します。 この名前は、ネットワーク上のフェールオーバー クラスター インスタンスを識別します。  
  
 既定のインスタンスまたは名前付きインスタンス - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスと名前付きインスタンスのどちらをインストールするか決定する場合は、次の事項を考慮してください。  
  
-   データベース サーバー上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の単独のインスタンスをインストールする場合は、そのインスタンスは既定のインスタンスであることが必要です。  
  
-   同じコンピューターで複数のインスタンスの使用を計画している場合は、名前付きインスタンスを使用します。 1 台のサーバーでは、既定のインスタンスを 1 つしかホストできません。  
  
-   [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] をインストールするアプリケーションでは、名前付きインスタンスとしてインストールする必要があります。 これにより、複数のアプリケーションが同じコンピューターにインストールされた場合に競合が発生する可能性が軽減されます。  
  
 **[既定のインスタンス]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスをインストールするには、このオプションを選択します。 1 台のコンピューターでホストできる既定のインスタンスは 1 つだけです。その他すべては名前付きインスタンスにする必要があります。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスをインストールしている場合は、その同じコンピューターに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のインスタンスを追加できます。  
  
 **[名前付きインスタンス]**  
 新しい名前付きインスタンスを作成するには、このオプションを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに名前を付ける際は、次の点に注意してください。  
  
-   インスタンス名では大文字と小文字が区別されません。  
  
-   インスタンス名の先頭または末尾にアンダースコア (_) を使用することはできません。  
  
-   インスタンス名には、"Default" などの予約されたキーワードを含めることはできません。 予約されたキーワードをインスタンス名に使用すると、セットアップ エラーが発生します。 詳細については、「[予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)」を参照してください。  
  
-   インスタンス名として MSSQLServer を指定すると、既定のインスタンスが作成されます。  
  
-   [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)] は、常に '[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]' の名前付きインスタンスとしてインストールされます。 この機能ロール用に別のインスタンス名を指定できます。  
  
-   インスタンス名は最大 16 文字まで指定できます。  
  
-   インスタンス名の先頭は文字にする必要があります。 使用できる文字は、Unicode 規格 2.0 で定義されている文字です。 これには、ラテン文字 a ～ z と A ～ Z、および各国言語の文字が含まれます。  
  
-   2 文字目以降では、Unicode 規格 2.0 で定義されている文字、Basic Latin またはその他言語の 10 進数、ドル記号 ($)、アンダースコア (_) を使用できます。  
  
-   埋め込み型スペースなどの特殊文字は、インスタンス名に使用できません。 円記号 (\\)、コンマ (,)、コロン (:)、セミコロン (;)、単一引用符 (')、アンパサンド (&)、ハイフン (-)、およびアット マーク (@) も使用できません。  
  
     現在の Windows コード ページで有効な文字だけを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名に使用できます。 サポートされていない Unicode 文字を使用すると、セットアップ エラーが発生します。  
  
 **検出されたインスタンスと機能**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行中のコンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスとコンポーネントが一覧表示されます。  
  
 **[インスタンス ID]** : 既定では、インスタンス名がインスタンス ID として使用されます。 これは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのインストール ディレクトリとレジストリ キーを識別するために使用されます。 これは、既定のインスタンスの場合も名前付きインスタンスの場合も同様です。 既定のインスタンスの場合、インスタンス名とインスタンス ID は、MSSQLSERVER になります。 既定以外のインスタンス ID を使用するには、 **Instance ID** フィールドで指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep では、このページに表示されるインスタンス ID は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep プロセスのイメージの準備手順で指定したインスタンス ID です。 イメージの完了手順では別のインスタンス ID を指定できません。  
  
> [!NOTE]  
>  アンダースコア (_) で始まるインスタンス ID や、シャープ記号 (#) またはドル記号 ($) を含むインスタンス ID はサポートされません。  
  
 ディレクトリ、ファイルの場所、およびインスタンス ID の名前付けの詳細については、「[SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](file-locations-for-default-and-named-instances-of-sql-server.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスを構成するすべてのコンポーネントは 1 つの単位として管理されます。 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack とアップグレードは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの各コンポーネントに適用されます。  
  
 同じインスタンス名を持つすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、次の条件を満たす必要があります。  
  
-   **同じバージョン**  
  
-   **同じエディション**  
  
-   **同じ言語設定**  
  
-   **同じクラスター状態**  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] はクラスターに対応していません。  
  
-   **同じオペレーティング システム**  
  
## <a name="analysis-services-configuration---account-provisioning"></a>Analysis Services の構成 - アカウントの準備
  このページを使用すると、サーバー モードを設定し、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] への無制限アクセスを必要とするユーザーまたはサービスに管理権限を付与することができます。 セットアップでは、ローカル Windows グループ BUILTIN\Administrators が、インストールするインスタンスの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー管理者ロールに自動的に追加されません。 サーバー管理者ロールにローカルの Administrators グループを追加する場合は、そのグループを明示的に指定する必要があります。  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールする場合は、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] サーバーの配置に責任を負う SharePoint ファーム管理者またはサービス管理者に管理権限を付与してください。  
  
### <a name="options"></a>オプション  
 **[サーバー モード]** - サーバー モードでは、サーバーに配置できる Analysis Services データベースの種類を指定します。 セットアップ中に指定したサーバー モードを後で変更することはできません。 各モードは互いに排他的です。そのため、従来の OLAP ソリューションとテーブル モデル ソリューションの両方をサポートする場合は、それぞれ異なるモードで構成した 2 つの Analysis Services のインスタンスが必要になります。  
  
 **[管理者の指定]** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのサーバー管理者を少なくとも 1 人指定する必要があります。 指定したユーザーまたはグループは、インストールする [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー管理者ロールのメンバーになります。 これらは、ソフトウェアをインストールするコンピューターと同じドメインの Windows ドメイン ユーザー アカウントである必要があります。  
  
> [!NOTE]  
>  ユーザー アカウント制御 (UAC) は Windows セキュリティ機能であり、管理操作または管理アプリケーションの承認を管理者が実行前に明示的に行う必要があります。 UAC は既定でオンになっているため、高度な特権を必要とする特定の操作について許可するよう求めるメッセージが表示されます。 UAC を構成して既定の動作を変更することも、特定のプログラム用に UAC をカスタマイズすることもできます。 UAC および UAC 構成の詳細については、「[User Account Control Step by Step Guide](https://go.microsoft.com/fwlink/?linkid=196350)」(Windows ユーザー アカウント制御手順ガイド) と「[User Account Control (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351)」(ユーザー アクセス制御) を参照してください。  
  
### <a name="see-also"></a>参照  
 [サービス アカウントの構成 &#40;Analysis Services#41;](../../analysis-services/instances/configure-service-accounts-analysis-services.md) [Windows サービス アカウントと権限の構成 ](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  

 ## <a name="analysis-services-configuration---data-directories"></a>Analysis Services の構成 - データ ディレクトリ
  次の表にある既定のディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。 これらのファイルにアクセスする権限は、ローカル管理者と、セットアップ中に作成されて準備される SQLServerMSASUser$\<インスタンス> セキュリティ グループのメンバーに付与されます。  
  
### <a name="uielement-list"></a>UI 要素の一覧  
  
|[説明]|既定のディレクトリ|推奨事項|  
|-----------------|-----------------------|---------------------|  
|データ ルート ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Data\ |\Program files\Microsoft SQL Server\ フォルダーが権限の制限により保護されていることを確認してください。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパフォーマンスは、多くの構成で、データ ディレクトリが配置されているストレージのパフォーマンスに依存します。 このディレクトリは、システムに割り当てられている中でパフォーマンスが最も高いストレージに配置してください。 フェールオーバー クラスターのインストールの場合は、データ ディレクトリが共有ディスク上に配置されるようにしてください。|  
|ログ ファイル ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Log\ |このディレクトリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログ ファイルのディレクトリであり、FlightRecorder ログを含んでいます。 フライト レコーダーの時間を増加する場合、ログ ディレクトリに十分な容量があることを確認してください。|  
|Temp ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Temp\ |Temp ディレクトリは、高パフォーマンスのストレージ サブシステムに配置してください。|  
|バックアップ ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Backup\ |このディレクトリは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のバックアップ ファイルのディレクトリです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールでは、ここは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] システム サービスが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ファイルをキャッシュする場所でもあります。<br /><br /> データの損失を防ぐために適切な権限を設定し、バックアップ ディレクトリに書き込むための適切な権限が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのユーザー グループに付与されるようにしてください。 マップされたドライブをバックアップ ディレクトリに使用することはサポートされていません。|  
  
### <a name="notes"></a>注  
  
-   SharePoint ファームに配置された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、アプリケーション ファイル、データ ファイル、およびコンテンツ データベースのプロパティとサービス アプリケーション データベースのプロパティを格納します。  
  
-   既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。  

-   SQL Server のフォルダーおよびファイルの種類を除外するように、ウイルス対策アプリケーションやスパイウェア対策アプリケーションなどのスキャン ソフトウェアを構成することが必要な場合があります。 詳細については、「[SQL Server を実行しているコンピューター上で実行するウイルス対策ソフトウェア](https://support.microsoft.com/kb/309422)」のサポート記事を参照してください。
  
-   既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、別のディレクトリにインストールする必要もあります。  
  
-   次の状況では、プログラム ファイルとデータ ファイルをインストールすることができません。  
  
    -   リムーバブル ディスク ドライブ  
  
    -   圧縮を使用したファイル システム  
  
    -   システム ファイルが配置されているディレクトリ  
  
### <a name="see-also"></a>参照  
 ディレクトリ、ファイルの場所、およびインスタンス ID の名前付けの詳細については、「[SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](file-locations-for-default-and-named-instances-of-sql-server.md)」を参照してください。  
  
## <a name="database-engine-configuration---data-directories"></a>データベース エンジンの構成 - データ ディレクトリ
  このページを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] のプログラムおよびデータ ファイルのインストール場所を指定します。 インストールの種類により、サポートされるストレージにはローカル ディスク、共有ストレージ、または SMB ファイル サーバーが含まれる場合があります。  
  
 SMB ファイル共有をディレクトリとして指定するには、サポートされている UNC パスを手動で入力する必要があります。 SMB ファイル共有を参照して指定することはできません。 SMB ファイル共有のサポートされる UNC パス形式は、" \\\Servername\ShareName\\..." です。  
  
### <a name="stand-alone-instance-of-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンス  
 次の表は、サポートされているストレージの種類と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスで使用される既定のディレクトリの一覧です。これらのディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。  
  
### <a name="uielement-list"></a>UI 要素の一覧  
  
|[説明]|サポートされているストレージの種類|既定のディレクトリ|推奨事項|  
|-----------------|----------------------------|-----------------------|---------------------|  
|データ ルート ディレクトリ|ローカル ディスク、SMB ファイル サーバー、共有ストレージ* |C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\ |[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。|  
|ユーザー データベース ディレクトリ|ローカル ディスク、SMB ファイル サーバー、共有ストレージ*|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data |ユーザー データ ディレクトリのベスト プラクティスは、ワークロードとパフォーマンスの要件によって異なります。|  
|ユーザー データベース ログ ディレクトリ|ローカル ディスク、SMB ファイル サーバー、共有ストレージ*|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data|ログ ディレクトリに十分な領域があることを確認してください。|  
|バックアップ ディレクトリ|ローカル ディスク、SMB ファイル サーバー、共有ストレージ*|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Backup|データの損失を防ぐために適切な権限を設定して、バックアップ ディレクトリに書き込むための適切な権限が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスのユーザー アカウントにあることを確認してください。 マップされたドライブをバックアップ ディレクトリに使用することはサポートされていません。|  
  
 *共有ディスクがサポートされていますが、これは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスで推奨される方法ではありません。  
  
### <a name="failover-cluster-instance-of-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンス  
 次の表は、サポートされているストレージの種類と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスで使用される既定のディレクトリの一覧です。これらのディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。  
  
|[説明]|サポートされているストレージの種類|既定のディレクトリ|推奨事項|  
|-----------------|----------------------------|-----------------------|---------------------|  
|データ ルート ディレクトリ|共有ストレージ、SMB ファイル サーバー|\<ドライブ>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。|  
|ユーザー データベース ディレクトリ|共有ストレージ、SMB ファイル サーバー|\<Drive:>Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|ユーザー データ ディレクトリのベスト プラクティスは、ワークロードとパフォーマンスの要件によって異なります。|  
|ユーザー データベース ログ ディレクトリ|共有ストレージ、SMB ファイル サーバー|\<Drive:>\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|ログ ディレクトリに十分な領域があることを確認してください。|  
|バックアップ ディレクトリ|ローカル ディスク、共有ストレージ、SMB ファイル サーバー|\<Drive:>\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Backup<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|データの損失を防ぐために適切な権限を設定して、バックアップ ディレクトリに書き込むための適切な権限が SQL Server サービスのユーザー アカウントにあることを確認してください。 マップされたドライブをバックアップ ディレクトリに使用することはサポートされていません。|  
  
### <a name="security-considerations"></a>セキュリティに関する考慮事項  
 セットアップにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。  
  
 次の推奨事項は SMB ファイル サーバーに当てはまります。  
  
-   SMB ファイル サーバーを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントはドメイン アカウントである必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに使用するアカウントには、データ ディレクトリとして使用する SMB ファイル共有フォルダーに対するフル コントロールの NTFS 権限が必要です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに使用するアカウントには、SMB ファイル サーバーに対する SeSecurityPrivilege 特権を付与する必要があります。 この特権を付与するには、ファイル サーバーで [ローカル セキュリティ ポリシー] コンソールを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査とセキュリティ ログの管理 **ポリシーに** セットアップ アカウントを追加します。 この設定は、 **[ローカル セキュリティ ポリシー]** コンソールの **[ローカル ポリシー]** にある **[ユーザー権利の割り当て]** セクションで行うことができます。  
  
### <a name="notes"></a>注  
  
-   既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。  
  
-   既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、別のディレクトリにインストールする必要もあります。  
  
-   次の状況では、プログラム ファイルとデータ ファイルをインストールすることができません。  
  
    -   リムーバブル ディスク ドライブ  
  
    -   圧縮を使用したファイル システム  
  
    -   システム ファイルが配置されているディレクトリ  
  
    -   フェールオーバー クラスター インスタンス上のマップされたネットワーク ドライブ  
  
### <a name="see-also"></a>参照  
### <a name="analysis-services-configuration---data-directories"></a>Analysis Services の構成 - データ ディレクトリ
  次の表にある既定のディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。 これらのファイルにアクセスする権限は、ローカル管理者と、セットアップ中に作成されて準備される SQLServerMSASUser$\<インスタンス> セキュリティ グループのメンバーに付与されます。  
  
#### <a name="uielement-list"></a>UI 要素の一覧  
  
|[説明]|既定のディレクトリ|推奨事項|  
|-----------------|-----------------------|---------------------|  
|データ ルート ディレクトリ |C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Data |\Program files\Microsoft SQL Server\ フォルダーが権限の制限により保護されていることを確認してください。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパフォーマンスは、多くの構成で、データ ディレクトリが配置されているストレージのパフォーマンスに依存します。 このディレクトリは、システムに割り当てられている中でパフォーマンスが最も高いストレージに配置してください。 フェールオーバー クラスターのインストールの場合は、データ ディレクトリが共有ディスク上に配置されるようにしてください。|  
|ログ ファイル ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Log |このディレクトリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログ ファイルのディレクトリであり、FlightRecorder ログを含んでいます。 フライト レコーダーの時間を増加する場合、ログ ディレクトリに十分な容量があることを確認してください。|  
|Temp ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Temp |Temp ディレクトリは、高パフォーマンスのストレージ サブシステムに配置してください。|  
|バックアップ ディレクトリ|C:\Program Files\Microsoft SQL Server\MSAS*nn*.\<InstanceID>\OLAP\Backup |このディレクトリは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の既定のバックアップ ファイルのディレクトリです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールでは、ここは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] システム サービスが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ファイルをキャッシュする場所でもあります。<br /><br /> データの損失を防ぐために適切な権限を設定し、バックアップ ディレクトリに書き込むための適切な権限が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのユーザー グループに付与されるようにしてください。 マップされたドライブをバックアップ ディレクトリに使用することはサポートされていません。|  
  
#### <a name="notes"></a>注  
  
-   SharePoint ファームに配置された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、アプリケーション ファイル、データ ファイル、およびコンテンツ データベースのプロパティとサービス アプリケーション データベースのプロパティを格納します。  
  
-   既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。  

-   SQL Server のフォルダーおよびファイルの種類を除外するように、ウイルス対策アプリケーションやスパイウェア対策アプリケーションなどのスキャン ソフトウェアを構成することが必要な場合があります。 詳細については、「[SQL Server を実行しているコンピューター上で実行するウイルス対策ソフトウェア](https://support.microsoft.com/kb/309422)」のサポート記事を参照してください。
  
-   既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、別のディレクトリにインストールする必要もあります。  
  
-   次の状況では、プログラム ファイルとデータ ファイルをインストールすることができません。  
  
    -   リムーバブル ディスク ドライブ  
  
    -   圧縮を使用したファイル システム  
  
    -   システム ファイルが配置されているディレクトリ  
  
#### <a name="see-also"></a>参照  
 ディレクトリ、ファイルの場所、およびインスタンス ID の名前付けの詳細については、「[SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](file-locations-for-default-and-named-instances-of-sql-server.md)」を参照してください。  
  
    
 [ファイル サーバーの共有アクセス許可と NTFS アクセス許可](https://go.microsoft.com/fwlink/?LinkID=206571) 

## <a name="database-engine-configuration---filestream"></a>データベース エンジンの構成 - Filestream
  このページを使用すると、このインストールの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に対して FILESTREAM を有効にすることができます。 FILESTREAM は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] varbinary(max) **BLOB (バイナリ ラージ オブジェクト) データをファイル システム上のファイルとして格納することにより、** と NTFS ファイル システムを統合します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、FILESTREAM データの挿入、更新、クエリ、検索、およびバックアップを行うことができます。 Win32 ファイル システム インターフェイスによるデータへのストリーミング アクセスが可能になります。  
  
### <a name="uielement-list"></a>UI 要素の一覧  
 **[Transact-SQL アクセスに対して FILESTREAM を有効にする]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする場合にオンにします。 他のコントロール オプションを使用できるようにするには、先にこのコントロールをオンにする必要があります。  
  
 **[ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]**  
 FILESTREAM の Win32 ストリーム アクセスを有効にする場合にオンにします。  
  
 **[Windows 共有名]**  
 このコントロールは、FILESTREAM データを格納する Windows 共有の名前を入力する場合に使用します。  
  
 **[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]**  
 このコントロールは、リモート クライアントにこのサーバー上のこの FILESTREAM データへのアクセスを許可する場合にオンにします。  
  
### <a name="see-also"></a>参照  
 [FILESTREAM の有効化と構成](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  

  
## <a name="database-engine-configuration---server-configuration"></a>データベース エンジンの構成 - サーバー構成
  このページは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ モードを設定し、Windows ユーザーまたはグループを [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の管理者として追加するために使用します。  
  
### <a name="considerations-for-running-includesscurrentincludessscurrent-mdmd"></a>[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の実行に関する注意点  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 **のログインとして** BUILTIN\Administrators [!INCLUDE[ssDE](../../includes/ssde-md.md)] グループが準備され、ローカル Administrators グループのメンバーは、管理者資格情報を使用してログインできました。 しかし、引き上げられたアクセス許可を使用するのはベスト プラクティスではありません。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 **BUILTIN\Administrators** グループはログインとして準備されていません。 したがって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しいインスタンスのインストール時に、管理ユーザーごとに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ログインを作成し、そのログインを sysadmin 固定サーバー ロールに追加する必要があります。 また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行に使用する Windows アカウントに対しても、同様の操作を行う必要があります。 それらのジョブには、レプリケーション エージェント ジョブも含まれます。  
  
### <a name="options"></a>オプション  
 **[セキュリティ モード]** : インストール用に Windows 認証または混合モード認証を選択します。  
  
 **[Windows プリンシパルの準備]** : 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、Windows の Builtin\Administrator ローカル グループが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin サーバー ロールに配置されました。これは、Windows 管理者に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスへのアクセス許可を付与する効果的な方法でした。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、Builtin\Administrator グループは sysadmin  サーバー ロールで提供されません。 代わりに、セットアップ時に新規インストール用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者を明示的に用意する必要があります。  
  
> [!IMPORTANT]  
>  セットアップ時に新規インストール用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者を明示的に用意する必要があります。 セットアップは、この手順を完了するまで続行できません。  
  
 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者の指定]**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの Windows プリンシパルを少なくとも 1 つ指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行しているアカウントを追加するには、**[現在のユーザー]** ボタンをクリックします。 システム管理者の一覧に対してアカウントを追加または削除するには、 **[追加]** または **[削除]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスについて管理者特権を持っているユーザー、グループ、またはコンピューターの一覧を編集します。  
  
 一覧の編集が完了したら、 **[OK]** をクリックし、構成ダイアログ ボックスで管理者の一覧を確認します。 一覧が完成したら、 **[次へ]** をクリックします。  
  
 混合モード認証を選択した場合は、組み込みの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者 (SA) アカウントのログオン資格情報を入力する必要があります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 **Windows 認証モード**  
 Windows ユーザー アカウントでユーザーが接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はオペレーティング システムの Windows プリンシパル トークンを使用してアカウント名とパスワードを検証します。 これは既定の認証モードで、混合モードよりはるかに安全性に優れています。 Windows 認証では、Kerberos セキュリティ プロトコルを利用し、強力なパスワードに対して複雑な検証を行うという点で、パスワード ポリシーが強化されています。また、アカウント ロックアウトの機能を提供し、パスワード有効期限にも対応しています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]sa パスワードを空白のままにしないでください。また、推測しやすいパスワードを設定しないでください。  
  
 **混合モード (Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証)**  
 Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用してユーザー接続を許可します。 Windows ユーザー アカウントで接続するユーザーは、Windows によって検証される信頼関係接続を使用することができます。  
  
 混合モード認証を選択する必要があり、レガシ アプリケーションに対応するために SQL ログインを使用する必要もある場合は、必ずすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントに強力なパスワードを設定してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証は旧バージョンとの互換性を維持するためだけに提供されます。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 **パスワードの入力**  
 システム管理者 (sa) ログインを入力および確認します。 パスワードは侵入者に対する防御の最前線であるため、システムのセキュリティにとって強力なパスワードを設定することは不可欠です。 sa パスワードを空白のままにしないでください。また、推測しやすいパスワードを設定しないでください。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パスワードは、文字、記号、数字の組み合わせを含む 1 ～ 128 文字で指定できます。 混合モード認証を選択する場合、インストール ウィザードの次のページに進む前に、強力な sa パスワードを入力する必要があります。  
  
 **強力なパスワードのガイドライン**  
 強力なパスワードとは、他人によってたやすく推測されず、コンピューター プログラムを使用して簡単にはハッキングされないパスワードです。 強力なパスワードでは、次のような禁止された条件または用語を使用することはできません。  
  
-   空白または NULL 条件  
  
-   "Password"  
  
-   "Admin"  
  
-   "Administrator"  
  
-   "sa"  
  
-   "sysadmin"  
  
 強力なパスワードには、インストール コンピューターに関連付けられた次のような用語を指定できません。  
  
-   現在、マシンにログオンしているユーザーの名前  
  
-   コンピューター名  
  
 強力なパスワードは、長さ 9 文字以上で、以下の 4 つの条件のうち 3 つ以上を満たしている必要があります。  
  
-   大文字を含んでいる。  
  
-   小文字を含んでいる。  
  
-   数字を含んでいる。  
  
-   #、%、^ など、英数字以外の文字を含んでいる。  
  
 このページで入力するパスワードは、強力なパスワード ポリシーの要件を満たす必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したオートメーションを使用している場合、必ず強力なパスワード ポリシーの要件を満たすパスワードを指定してください。  
  
### <a name="related-content"></a>関連コンテンツ  
 Windows 認証と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]詳細については、「[認証モードの選択](../../relational-databases/security/choose-an-authentication-mode.md)」をご覧ください。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を実行するアカウントの選択の詳細については、「[Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」をご覧ください。
  
## <a name="database-engine-configuration---tempdb"></a>データベース エンジンの構成 - TempDB
  このページを利用し、**tempdb** のデータとログ ファイルの場所、サイズ、拡張設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] のファイル数を指定します。 インストールの種類により、サポートされるストレージにはローカル ディスク、共有ストレージ、または SMB ファイル サーバーが含まれる場合があります。  
  
 SMB ファイル共有をディレクトリとして指定するには、サポートされている UNC パスを手動で入力する必要があります。 SMB ファイル共有を参照して指定することはできません。 SMB ファイル共有のサポートされる UNC パス形式は、" \\\Servername\ShareName\\..." です。  
  
### <a name="data-and-log-directories-for--a-stand-alone-instance-of--includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスのデータとログのディレクトリ  
 次の表は、サポートされているストレージの種類と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスの既定のディレクトリの一覧です。ディレクトリは、セットアップ中に構成できます。  
  
|[説明]|サポートされているストレージの種類|既定のディレクトリ|推奨事項|  
|-----------------|----------------------------|-----------------------|---------------------|  
|**データ ディレクトリ**|ローカル ディスク、SMB ファイル サーバー、共有ストレージ* |C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。<br /><br /> **temdb** ディレクトリのベスト プラクティスは、ワークロードとパフォーマンスの要件によって異なります。 複数のフォルダー/ドライブを指定し、データ ファイルを複数のボリュームに分散します。|  
|**ログ ディレクトリ**|ローカル ディスク、SMB ファイル サーバー、共有ストレージ*|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data|ログ ディレクトリに十分な領域があることを確認してください。|  
  
 *共有ディスクがサポートされていますが、これは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスタンドアロン インスタンスで推奨される方法ではありません。  
  
### <a name="data-and-log-directories-for-a-failover-cluster-instance-of-includessnoversionincludesssnoversion-mdmd"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスのデータとログのディレクトリ  
 次の表は、サポートされているストレージの種類と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスで使用される既定のディレクトリの一覧です。これらのディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。  
  
|[説明]|サポートされているストレージの種類|既定のディレクトリ|推奨事項|  
|-----------------|----------------------------|-----------------------|---------------------|  
|**tempdb** データ ディレクトリ|ローカル ディスク、共有ストレージ、SMB ファイル サーバー|\<Drive:>\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\Data<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。<br /><br /> 指定のディレクトリ (複数のファイルが指定される場合、ディレクトリも複数になります) はすべてのクラスター ノードで有効にします。 フェールオーバー中に、 **tempdb** のディレクトリがフェールオーバーのターゲット ノード上で利用できない場合、SQL Server リソースはオンラインへの移行に失敗します。|  
|**tempdb** ログ ディレクトリ|ローカル ディスク、共有ストレージ、SMB ファイル サーバー|\<Drive:>\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL*nn*.\<InstanceID>\MSSQL\Data<br /><br /> ヒント:**[クラスター ディスクの選択]** ページで共有ディスクを選択した場合、既定値は最初の共有ディスクになります。 **[クラスター ディスクの選択]** ページで何も選択しなかった場合、このフィールドの既定値は空白になります。|ユーザー データ ディレクトリのベスト プラクティスは、ワークロードとパフォーマンスの要件によって異なります。<br /><br /> 指定したディレクトリがすべてのクラスター ノードで有効であることを確認してください。 フェールオーバー中に、 **tempdb** のディレクトリがフェールオーバーのターゲット ノード上で利用できない場合、SQL Server リソースはオンラインへの移行に失敗します。<br /><br /> ログ ディレクトリに十分な領域があることを確認してください。|  
  
### <a name="uielement-list"></a>UI 要素の一覧  
 作業負荷と要件に合わせて **tempdb** の設定を構成します。 次の設定は、 **tempdb** データ ファイルに適用されます。  
  
-   **ファイル数** は **tempdb**のデータ ファイルの合計数です。 既定値は 8 とセットアップ時に検出された論理コア数の小さいほうになります。 一般的なルールとして、論理プロセッサの数が 8 以下の場合、論理プロセッサと同じ数のデータ ファイルを使用します。 論理プロセッサの数が 8 より大きい場合、8 つのデータ ファイルを使用し、競合が続く場合、競合が許容できるレベルに減少するまでデータ ファイルの数を 4 の倍数 (最大で論理プロセッサの数) 分増やすか、ワークロード/コードを変更します。 
  
-   **初回サイズ (MB)** は各 **tempdb** データ ファイルの初回サイズです (MB 単位)。 既定値は 8 MB です (または、[!INCLUDE[ssexpress](../../includes/ssexpress_md.md)] の場合は 4 MB)。 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] では、最大初期ファイル サイズ 262,144 MB (256 GB) が導入されます。 [!INCLUDE[sssql15](../../includes/sssql15-md.md)] の最大初期ファイル サイズは 1024 MB でした。 すべての **tempdb** データ ファイルの初回サイズは同じです。 **tempdb** は SQL Server が起動するか、フェーズするたびに再作成されるため、通常の作業のワークロードに必要なサイズに近いサイズを指定する必要があります。 起動時にさらに効率的に **tempdb** を作成するには、 [[データベースのファイルの瞬時初期化]](../../relational-databases/databases/database-instant-file-initialization.md)を有効にします。  
  
-   **合計初回サイズ (MB)** はすべての **tempdb** データ ファイルを合計したものです。  
  
-   **自動拡張 (MB)** はメガバイト単位で表した領域です。各 **tempdb** データ ファイルの領域が枯渇すると、このサイズ分だけ自動的に拡張します。 [!INCLUDE[sssql15](../../includes/sssql15-md.md)] 以降では、すべてのデータ ファイルがこの設定で指定された量だけ同時に拡張します。  
  
-   **自動拡張の合計 (MB)** は各自動拡張イベントを合計したものです。  
  
-   **データ ディレクトリ** には、 **tempdb** データ ファイルを維持しているすべてのディレクトリが表示されます。 ディレクトリが複数存在するとき、データ ファイルはラウンド ロビン方式でディレクトリに置かれます。 たとえば、3 つのディレクトリを作成し、8 つのデータ ファイルを指定する場合、データ ファイル番号 1、4、7 が最初のディレクトリに作成されます。 データ ファイル番号 2、5、8 が 2 番目のディレクトリに作成されます。 データ ファイル番号 3 と 6 が 3 番目のディレクトリに入ります。  
  
-   ディレクトリを追加するには、 **[追加…]** をクリックします。  
  
-   ディレクトリを削除するには、ディレクトリを選択し、 **[削除]** をクリックします。  
  
 **TempDB ログ ファイル** はログ ファイルの名前です。 自動的に作成されます。 次の設定は、 **tempdb** ログ ファイルにのみ適用されます。  
  
-   **初回サイズ (MB)** は **tempdb** ログ ファイルの初回サイズです。 既定値は 8 MB です (または、[!INCLUDE[ssexpress](../../includes/ssexpress_md.md)] の場合は 4 MB)。 [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] では、最大初期ファイル サイズ 262,144 MB (256 GB) が導入されます。 [!INCLUDE[sssql15](../../includes/sssql15-md.md)] の最大初期ファイル サイズは 1024 MB でした。 **tempdb** は SQL Server が起動するか、フェーズするたびに再作成されるため、通常の作業のワークロードに必要なサイズに近いサイズを指定する必要があります。 起動時にさらに効率的に **tempdb** を作成するには、[[データベースのファイルの瞬時初期化]](../../relational-databases/databases/database-instant-file-initialization.md) を有効にします。  
  
-   **注記: Tempdb** では、最小ログ記録が利用されます。 **tempdb** ログはバックアップできません。 SQL Server が起動するたびに、あるいはクラスター インスタンスのフェールオーバー時に再作成されます。  
  
-   **自動拡張 (MB)** は **tempdb** ログの拡張単位であり、メガバイト単位で指定されます。  既定値の 64 MB で、初期化中、最適な数の仮想ログ ファイルが作成されます。  
  
-   **注記: Tempdb** ログ ファイルでは、ファイルの瞬時初期化は利用されません。  
  
-   **ログ ディレクトリ** は、 **tempdb** ログ ファイルが作成されるディレクトリです。 **tempdb** ログ ディレクトリは 1 つだけ存在します。  
  
### <a name="security-considerations"></a>セキュリティに関する考慮事項  
 セットアップにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディレクトリの ACL が構成され、構成の一部として継承が無効になります。  

 次の推奨事項は SMB ファイル サーバーに当てはまります。  
  
-   SMB ファイル サーバーを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントはドメイン アカウントである必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに使用するアカウントには、データ ディレクトリとして使用する SMB ファイル共有フォルダーに対するフル コントロールの NTFS 権限が必要です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールに使用するアカウントには、SMB ファイル サーバーに対する SeSecurityPrivilege 特権を付与する必要があります。 この特権を付与するには、ファイル サーバーで [ローカル セキュリティ ポリシー] コンソールを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査とセキュリティ ログの管理 **ポリシーに** セットアップ アカウントを追加します。 この設定は、 **[ローカル セキュリティ ポリシー]** コンソールの **[ローカル ポリシー]** にある **[ユーザー権利の割り当て]** セクションで行うことができます。  
  
### <a name="notes"></a>注  
  
-   既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、別のディレクトリにインストールする必要もあります。  
  
### <a name="see-also"></a>参照  
 [を含めて、すべての](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [ファイル サーバーの共有アクセス許可と NTFS アクセス許可](https://go.microsoft.com/fwlink/?LinkID=206571)  

## <a name="database-engine-configuration---user-instance"></a>データベース エンジンの構成 - ユーザー インスタンス
**[ユーザー インスタンス]** ページを使用して、管理者権限のないユーザー用に、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] の個別インスタンスを作成し、それらのユーザーを管理者ロールに追加します。  
  
### <a name="option"></a>オプション  
 [ユーザー インスタンスを有効にする]  
 既定値はオンです。 ユーザー インスタンス有効化の機能を無効にするには、このチェック ボックスをオフにします。  
  
 ユーザー インスタンスは子インスタンスまたはクライアント インスタンスとも呼ばれ、ユーザーに代わって親インスタンス ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] などのサービスを実行するプライマリ インスタンス) によって作成される [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のインスタンスです。 ユーザー インスタンスは、そのユーザーのセキュリティ コンテキストでのユーザーのプロセスとして実行します。 親インスタンスやコンピューター上で実行するその他のユーザー インスタンスとは分離されます。 ユーザー インスタンス機能は "通常のユーザーとして実行" (Run As Normal User: RANU) とも呼ばれます。  
  
> [!NOTE]  
>  セットアップ中に **sysadmin** 固定サーバー ロールのメンバーとして準備されたログインは、テンプレート データベース内の管理者として準備されます。 削除されない限り、これらはユーザー インスタンスのメンバー **sysadmin** 固定サーバー ロールです。  
  
 [ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者ロールに追加する]  
 既定値はオフです。 現在のセットアップ ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理者ロールに追加するには、このチェック ボックスをオンにします。  
  
 [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ユーザーのうち、BUILTIN\Administrators のメンバーは、[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] への接続時に sysadmin 固定サーバー ロールに自動的に追加されません。 サーバーレベルの管理者ロールに明示的に追加されている [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] ユーザーのみが、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]を管理できます。 Built-In\Users グループのすべてのメンバーが [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] インスタンスに接続できますが、データベース タスクの実行権限は制限されます。 このため、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 特権を以前のリリースの Windows の BUILTIN\Administrators および Built-In\Users から継承しているユーザーには、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] で実行している [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)]のインスタンスにおいて、管理特権を明示的に付与する必要があります。  
  
 このインストール プログラムの完了後にユーザー ロールに変更を加えるには、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] セキュリティ構成ツール (SQLSAC.exe) を使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者ロールのユーザー一覧を更新するには、 **[新しい管理者の追加]** リンクをクリックします。  
  
 **[準備するユーザー]** フィールドに、権限を更新するユーザーが DomainName\UserName 形式で表示されたことを確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [使用できる特権] **ペインの** インスタンスの一覧から、更新するロールを選択して、右矢印をクリックします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使用可能なすべてのインスタンスの、使用できるすべてのロールにユーザーを追加するには、二重右矢印をクリックします。  
  
 選択の完了後に変更を適用するには、[!INCLUDE[clickOK](../../includes/clickok-md.md)]変更を適用せずにツールを終了するには、**[キャンセル]** をクリックします。  
  
  
