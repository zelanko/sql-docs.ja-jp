---
title: バックアップ、復元、およびデータベース (XMLA) の同期 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d311a07eb11f1c5119a3c20d7536b5a2986b49
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145937"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>データベースのバックアップ、復元、および同期 (XMLA)
  XML for Analysis には、データベースのバックアップ、復元、および同期を行う 3 つのコマンドがあります。  
  
-   [バックアップ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)コマンドでバックアップを[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]バックアップ ファイル (.abf) をセクションで説明した[データベースのバックアップ](#backing_up_databases)します。  
  
-   [復元](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)コマンドは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  セクションで説明されているデータベースを .abf ファイルから[データベースの復元](#restoring_databases)します。  
  
-   [同期](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)コマンドでは、1 つは同期[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、セクションで説明した別のデータベースのメタデータとデータでデータベース[データベースの同期](#synchronizing_databases)します。  
  
##  <a name="backing_up_databases"></a> データベースのバックアップ  
 前に説明したように、**バックアップ**コマンドを指定したバックアップ[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイルにします。 **バックアップ**コマンドがさまざまなプロパティをバックアップするデータベースを指定するためには、セキュリティ定義、およびバックアップするリモート パーティションをバックアップする方法を使用するバックアップ ファイル。  
  
> [!IMPORTANT]  
>  Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。 また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 バックアップするデータベースを指定する設定、[オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、**バックアップ**コマンド。 **オブジェクト**プロパティは、データベースのオブジェクト識別子を含める必要がありますまたはエラーが発生します。  
  
 作成して、バックアップ プロセスによって使用されるファイルを指定する設定、[ファイル](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla)のプロパティ、**バックアップ**コマンド。 **ファイル**プロパティを作成するバックアップ ファイルの UNC パスとファイル名に設定する必要があります。  
  
 バックアップに使用するファイルの指定に加えて、指定したバックアップ ファイルに対する以下のオプションを設定できます。  
  
-   設定した場合、 [AllowOverwrite](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla)プロパティを true に、**バックアップ**コマンドでは、指定したファイルが既に存在する場合、バックアップ ファイルが上書きされます。 設定した場合、 **AllowOverwrite**プロパティを false に、指定したバックアップ ファイルが既に存在する場合にエラーが発生しました。  
  
-   設定した場合、 [ApplyCompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla)ファイルを作成した後、プロパティを true に、バックアップ ファイルが圧縮されています。  
  
-   設定した場合、[パスワード](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla)任意の空白以外の値、バックアップ ファイルにプロパティが指定したパスワードを使用して暗号化します。  
  
    > [!IMPORTANT]  
    >  場合**ApplyCompression**と**パスワード**プロパティが指定されていない場合、バックアップ ファイルがクリア テキストで接続文字列でユーザー名とパスワードに含まれるを格納します。 クリア テキストで格納されたデータは、取得される可能性があります。 セキュリティを強化を使用して、 **ApplyCompression**と**パスワード**両方に設定を圧縮し、バックアップ ファイルを暗号化します。  
  
### <a name="backing-up-security-settings"></a>セキュリティ設定のバックアップ  
 [セキュリティ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)プロパティかどうか、**バックアップ**コマンドで定義された、ロールや権限など、セキュリティ定義をバックアップ、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **セキュリティ**プロパティも、バックアップ ファイルが、Windows ユーザー アカウントとセキュリティ定義のメンバーとして定義されているグループに含めるかどうかを決定します。  
  
 値、**セキュリティ**プロパティは、次の表に示す文字列の 1 つに制限されています。  
  
|値|説明|  
|-----------|-----------------|  
|*skipMembership*|バックアップ ファイルにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|バックアップ ファイルにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|バックアップ ファイルからセキュリティ定義を除外します。|  
  
### <a name="backing-up-remote-partitions"></a>リモート パーティションのバックアップ  
 リモート パーティションをバックアップする、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、データベースを設定する、 [BackupRemotePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla)のプロパティ、**バックアップ**コマンドを true に設定します。 この設定により、**バックアップ**データベースのリモート パーティションを格納するために使用するリモート データ ソースごとにリモート バックアップ ファイルを作成するコマンド。  
  
 バックアップする各リモート データ ソースを含めることによって、対応するバックアップ ファイルを指定することができます、[場所](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla)内の要素、[場所](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla)のプロパティ、**バックアップ**コマンド。 **場所**要素があります、**ファイル**プロパティが、リモート バックアップ ファイルの UNC パスとファイル名に設定し、その[DataSourceID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceid-element-xmla)プロパティの識別子に設定データベースで定義されているリモート データ ソース。  
  
##  <a name="restoring_databases"></a> データベースの復元  
 **復元**コマンドは、指定した復元[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース バックアップ ファイルから。 **復元**コマンドがさまざまなプロパティをセキュリティ定義、格納するリモート パーティション、および再配置を復元する方法を使用するバックアップ ファイルを復元するデータベースを指定するためにはリレーショナル OLAP (ROLAP)オブジェクト。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 上書きする、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース、ユーザーには、次のロールのいずれかが必要: サーバー ロールのメンバー、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスまたは復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバー。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 **DatabaseName**のプロパティ、**復元**コマンドは、データベースのオブジェクト識別子を含める必要がありますまたはエラーが発生します。 指定されたデータベースが既に存在する場合、 **AllowOverwrite**プロパティは、既存のデータベースを上書きするかどうかを決定します。 場合、 **AllowOverwrite**プロパティが false に設定し、指定されたデータベースが既に存在するエラーが発生します。  
  
 設定する必要があります、**ファイル**のプロパティ、**復元**コマンドを指定したデータベースに復元するバックアップ ファイルの UNC パスとファイル名にします。 設定することも、**パスワード**指定したバックアップ ファイルのプロパティ。 場合、**パスワード**任意の空白以外の値に設定されて、バックアップ ファイルが指定したパスワードを使用して復号化します。 バックアップ ファイルが暗号化されていない場合、または指定されたパスワードがバックアップ ファイルの暗号化に使用されたパスワードと一致しない場合は、エラーが発生します。  
  
### <a name="restoring-security-settings"></a>セキュリティ設定の復元  
 **セキュリティ**プロパティを決定するかどうか、**復元**コマンドは、ロールで定義された権限など、セキュリティ定義を復元する[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **セキュリティ**プロパティも決定するかどうか、**復元**コマンドには、Windows ユーザー アカウントと、復元プロセスの一部として、セキュリティ定義のメンバーとして定義されているグループが含まれています。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*skipMembership*|データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|データベースからセキュリティ定義を除外します。|  
  
### <a name="restoring-remote-partitions"></a>リモート パーティションの復元  
 以前の中に作成されたリモート バックアップ ファイルごと**バックアップ**コマンドを含めることによって、関連付けられているリモート パーティションを復元する、**場所**内の要素、**場所**のプロパティ、**復元**コマンド。 [%Datasourcetype](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourcetype-element-xmla)プロパティごとに**場所**要素を除外または明示的に設定する必要があります*リモート*します。  
  
 指定された各**場所**要素、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスで指定されたリモート データ ソースの接続、 **DataSourceID**リモート バックアップ ファイルで定義されているパーティションを復元するプロパティ指定されている、**ファイル**プロパティ。 それに、 **DataSourceID**と**ファイル**プロパティでは、次のプロパティはそれぞれの使用可能な**場所**リモート パーティションを復元するための要素。  
  
-   指定されたリモート データ ソースの接続文字列を上書きする**DataSourceID**を設定することができます、 **ConnectionString**のプロパティ、**場所**要素を別の接続文字列。 **復元**コマンドに含まれている接続文字列を使用し、 **ConnectionString**プロパティ。 場合**ConnectionString**が指定されていない、**復元**コマンドは、指定されたリモート データ ソースのバックアップ ファイルに格納された接続文字列を使用します。 使用することができます、 **ConnectionString**別のリモート インスタンスにリモート パーティションを移動するには設定します。 ただし、使用することはできません、 **ConnectionString**復元されたデータベースを含む同じインスタンスにリモート パーティションを復元するには設定します。 つまり、使用することはできません、 **ConnectionString**プロパティをローカル パーティションのリモート パーティションを作成します。  
  
-   リモート データ ソースにリモート パーティションを格納するために使用元フォルダーごとに指定することができます、[フォルダー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla)元のフォルダーに格納されているすべてのリモート パーティションを復元するための新しいフォルダーを示す要素。 場合、**フォルダー**要素が指定されていない、**復元**コマンドはリモート バックアップ ファイルに含まれるリモート パーティションに指定された元のフォルダーを使用します。  
  
### <a name="relocating-rolap-objects"></a>ROLAP オブジェクトの再配置  
 **復元**コマンドは、集計や、基になるリレーショナル データ ソースのテーブルにこのような情報が格納されているために、ROLAP ストレージを使用するオブジェクトのデータを復元できません。 ただし、ROLAP オブジェクトのメタデータは復元できます。 ROLAP オブジェクトのメタデータを復元する、**復元**コマンドは、リレーショナル データ ソースにテーブル構造を再作成します。  
  
 使用することができます、**場所**内の要素を**復元**ROLAP オブジェクトを再配置するコマンド。 各**場所**、データ ソースを配置する場合に使用される要素、 **%datasourcetype**プロパティ明示的に設定する必要があります*ローカル*します。 設定する必要も、 **ConnectionString**のプロパティ、**場所**要素を新しい場所の接続文字列。 復元中、**復元**コマンドによって識別されるデータ ソースの接続文字列に置き換わります、 **DataSourceID**のプロパティ、**場所**要素値を持つ、 **ConnectionString**のプロパティ、**場所**要素。  
  
##  <a name="synchronizing_databases"></a> データベースの同期  
 **同期**データおよびメタデータを指定したコマンドでは同期[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を別のデータベースのデータベース。 **同期**コマンドには、ソース データベースを指定できるさまざまなプロパティをセキュリティ定義、同期するリモート パーティションと ROLAP オブジェクトの同期を同期する方法。  
  
> [!NOTE]  
>  **同期**サーバー管理者とデータベース管理者によってのみコマンドを実行できます。 同期元データベースと同期先のデータベースの両方の互換性レベルが同じであることが必要です。  
  
### <a name="specifying-the-source-database"></a>同期元データベースの指定  
 [ソース](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)のプロパティ、**同期**コマンドには、2 つのプロパティが含まれています。 **ConnectionString**と**オブジェクト**します。 **ConnectionString**プロパティが、ソース データベースを含むインスタンスの接続文字列を含む、**オブジェクト**プロパティには、ソース データベースのオブジェクト識別子が含まれています。  
  
 転送先データベースは、現在のデータベースをセッション、**同期**コマンドを実行します。  
  
 場合、 **ApplyCompression**のプロパティ、**同期**コマンドが設定されて送信される前に、転送先データベースにデータベースを圧縮ソースから送信される情報は、true にします。  
  
### <a name="synchronizing-security-settings"></a>セキュリティ設定の同期  
 [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)プロパティかどうか、**同期**コマンドは、ソース データベースで定義されたアクセス許可、ロールなど、セキュリティ定義を同期します。 **SynchronizeSecurity**プロパティも決定するかどうか、**では**コマンドには、Windows ユーザー アカウントとセキュリティ定義のメンバーとして定義されているグループが含まれています。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*skipMembership*|同期先データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|同期先データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|同期先データベースからセキュリティ定義を除外します。|  
  
### <a name="synchronizing-remote-partitions"></a>リモート パーティションの同期  
 ソース データベースに存在するリモート データ ソースごとに関連付けられている各リモート パーティションを同期を含めることによって、**場所**内の要素、**場所**のプロパティ、 **同期**コマンド。 各**場所**要素、 **%datasourcetype**プロパティを除外または明示的に設定する必要があります*リモート*します。  
  
 定義先のデータベース内のリモート データ ソースに接続し、**同期**コマンドで定義されている接続文字列を使用して、 **ConnectionString**のプロパティ、**場所**要素。 **同期**コマンドで使用し、 **DataSourceID**のプロパティ、**場所**を同期させるリモート パーティションを識別する要素。 **同期**コマンドで指定されたリモート データ ソース上のリモート パーティションを同期する、 **DataSourceID** で指定されたリモートデータソースとソースデータベースでのプロパティ**DataSourceID**先データベースのプロパティ。  
  
 ソース データベース上のリモート データ ソースにリモート パーティションを格納するために使用元フォルダーごとに指定することも、**フォルダー**内の要素、**場所**要素。 **フォルダー**要素が、リモート データ ソースの元のフォルダーに格納されているすべてのリモート パーティションを同期するための転送先データベースに新しいフォルダーを示します。 場合、**フォルダー**要素が指定されていない、Synchronize コマンドが指定されているソース データベースに格納されているリモート パーティションの元のフォルダーを使用します。  
  
### <a name="synchronizing-rolap-objects"></a>ROLAP オブジェクトの同期  
 **同期**コマンドは、集計や、基になるリレーショナル データ ソースのテーブルにこのような情報が格納されているために、ROLAP ストレージを使用するオブジェクトのデータを同期できません。 ただし、ROLAP オブジェクトのメタデータは同期できます。 メタデータを同期する、**同期**コマンドは、リレーショナル データ ソースにテーブル構造を再作成されます。  
  
 使用することができます、**場所**ROLAP オブジェクトを同期する同期コマンド内の要素。 各**場所**、データ ソースを配置する場合に使用される要素、 **%datasourcetype**プロパティ明示的に設定する必要があります*ローカル*します。 . 設定する必要も、 **ConnectionString**のプロパティ、**場所**要素を新しい場所の接続文字列。 同期中に、**同期**コマンドによって識別されるデータ ソースの接続文字列に置き換わります、 **DataSourceID**のプロパティ、**場所**値を持つ要素、 **ConnectionString**のプロパティ、**場所**要素。  
  
## <a name="see-also"></a>参照  
 [Backup 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [Restore 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [Synchronize 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
