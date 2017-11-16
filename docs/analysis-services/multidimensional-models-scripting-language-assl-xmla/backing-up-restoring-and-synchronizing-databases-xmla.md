---
title: "バックアップの復元、データベース、および同期 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- restoring databases [XML for Analysis]
- backing up databases [XML for Analysis]
- database backups [XML for Analysis]
- synchronization [XML for Analysis]
- database restores [XML for Analysis]
ms.assetid: 6c021b2e-6ad0-444e-b23f-4b5f72ce084b
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d64bc30a5d36d810e55d012fcd7fc302730a0ec
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>データベースのバックアップ、復元、および同期 (XMLA)
  XML for Analysis には、データベースのバックアップ、復元、および同期を行う 3 つのコマンドがあります。  
  
-   [バックアップ](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)コマンド バックアップ、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]バックアップ ファイル (.abf) のセクションで説明した[データベースのバックアップ](#backing_up_databases)です。  
  
-   [復元](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)復元のコマンド、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、セクションの説明に従って、.abf ファイルからデータベース[Restoring Databases](#restoring_databases)です。  
  
-   [同期](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)いずれかのコマンドでは同期[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のセクションで説明したデータと、別のデータベースのメタデータを使ってデータベース[データベースの同期](#synchronizing_databases)です。  
  
##  <a name="backing_up_databases"></a>データベースのバックアップ  
 以前に説明したように、**バックアップ**のコマンドは、指定したバックアップ[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイル。 **バックアップ**コマンドにはさまざまなプロパティをバックアップするデータベースを指定するため、セキュリティの定義、およびバックアップするリモート パーティションをバックアップする方法を使用するバックアップ ファイル。  
  
> [!IMPORTANT]  
>  Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。 また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 設定をバックアップするデータベースを指定する、[オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、**バックアップ**コマンド。 **オブジェクト**プロパティは、データベースのオブジェクト識別子を含める必要がありますまたはエラーが発生します。  
  
 設定を作成して、バックアップ プロセスで使用するには、ファイルを指定する、[ファイル](../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)のプロパティ、**バックアップ**コマンド。 **ファイル**プロパティを作成するバックアップ ファイルの UNC パスとファイル名に設定する必要があります。  
  
 バックアップに使用するファイルの指定に加えて、指定したバックアップ ファイルに対する以下のオプションを設定できます。  
  
-   設定した場合、 [AllowOverwrite](../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)プロパティを true に、**バックアップ**コマンドでは、指定したファイルが既に存在する場合、バックアップ ファイルが上書きされます。 設定した場合、 **AllowOverwrite**プロパティを false に、指定したバックアップ ファイルが既に存在する場合にエラーが発生しました。  
  
-   設定した場合、 [ApplyCompression](../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md)ファイルが作成された後に、プロパティを true、バックアップ ファイルには圧縮されます。  
  
-   設定した場合、[パスワード](../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)空白値、バックアップ ファイルにプロパティが指定したパスワードを使用して暗号化します。  
  
    > [!IMPORTANT]  
    >  場合**ApplyCompression**と**パスワード**プロパティが指定されていない場合、バックアップ ファイルがクリア テキストで接続文字列でユーザー名とパスワードに含まれるを格納します。 クリア テキストで格納されたデータは、取得される可能性があります。 セキュリティ強化のため、使用して、 **ApplyCompression**と**パスワード**設定を両方の圧縮し、バックアップ ファイルを暗号化します。  
  
### <a name="backing-up-security-settings"></a>セキュリティ設定のバックアップ  
 [セキュリティ](../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)プロパティを決定するかどうか、**バックアップ**コマンドで定義されたロールや権限など、セキュリティ定義をバックアップ、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **セキュリティ**プロパティはまた、バックアップ ファイルが Windows ユーザー アカウントと、セキュリティ定義のメンバーとして定義されているグループに含めるかどうかを決定します。  
  
 値、**セキュリティ**プロパティは、次の表に示す文字列の 1 つに制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*SkipMembership*|バックアップ ファイルにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|バックアップ ファイルにセキュリティ定義とメンバーシップ情報を含めます。|  
|*Ignoresecurity のいずれか*|バックアップ ファイルからセキュリティ定義を除外します。|  
  
### <a name="backing-up-remote-partitions"></a>リモート パーティションのバックアップ  
 リモート パーティションをバックアップするには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、データベースを設定する、 [BackupRemotePartitions](../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)のプロパティ、**バックアップ**コマンドを true に設定します。 この設定により、**バックアップ**コマンドは、データベースのリモート パーティションの格納に使用するリモート データ ソースごとにリモート バックアップ ファイルを作成します。  
  
 バックアップする各リモート データ ソースを指定できます、対応するバックアップ ファイルを含めることによって、[場所](../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)内の要素、[場所](../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)のプロパティ、**バックアップ**コマンド。 **場所**持つ要素があります、**ファイル**プロパティ、リモート バックアップ ファイルの UNC パスとファイル名に設定して、その[DataSourceID](../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)プロパティの識別子に設定します。データベースで定義されているリモート データ ソース。  
  
##  <a name="restoring_databases"></a>データベースの復元  
 **復元**コマンドは、指定した復元[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース バックアップ ファイルからです。 **復元**コマンドはさまざまなプロパティをセキュリティ定義、リモート パーティションを格納して、再配置を復元する方法を使用するバックアップ ファイルを復元するデータベースを指定するためにはリレーショナル OLAP (ROLAP)オブジェクト。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 上書きする、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース、ユーザーには、次のロールのいずれかが必要: サーバー ロールのメンバー、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスまたは復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーです。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 **DatabaseName**のプロパティ、**復元**コマンドは、データベースのオブジェクト識別子を含める必要がありますまたはエラーが発生します。 指定されたデータベースが既に存在する場合、 **AllowOverwrite**プロパティは、既存のデータベースを上書きするかどうかを決定します。 場合、 **AllowOverwrite**プロパティが false に設定し、指定されたデータベースが既に存在するエラーが発生します。  
  
 設定する必要があります、**ファイル**のプロパティ、**復元**コマンドを指定されたデータベースを復元するバックアップ ファイルの UNC パスとファイル名にします。 設定することも、**パスワード**指定したバックアップ ファイルのプロパティです。 場合、**パスワード**プロパティが空白でない値に、指定したパスワードを使用して、バックアップ ファイルの暗号化を解除します。 バックアップ ファイルが暗号化されていない場合、または指定されたパスワードがバックアップ ファイルの暗号化に使用されたパスワードと一致しない場合は、エラーが発生します。  
  
### <a name="restoring-security-settings"></a>セキュリティ設定の復元  
 **セキュリティ**プロパティを決定するかどうか、**復元**コマンドは、ロールや権限で定義されているなど、セキュリティ定義を復元、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 **セキュリティ**プロパティも決定するかどうか、**復元**コマンドには、Windows ユーザー アカウントと、復元プロセスの一部として、セキュリティ定義のメンバーとして定義されているグループが含まれています。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*SkipMembership*|データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*Ignoresecurity のいずれか*|データベースからセキュリティ定義を除外します。|  
  
### <a name="restoring-remote-partitions"></a>リモート パーティションの復元  
 以前の中に作成されたリモート バックアップ ファイルごとに**バックアップ**コマンドを含めることによって、関連付けられているリモート パーティションを戻すことができます、**場所**内の要素、**場所**のプロパティ、**復元**コマンド。 [%Datasourcetype](../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)それぞれのプロパティ**場所**要素を除外または明示的に設定する必要があります*リモート*です。  
  
 指定された各**場所**要素、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスで指定されたリモート データ ソースの接続、 **DataSourceID**リモート バックアップ ファイルで定義されたパーティションを復元するプロパティ指定されている、**ファイル**プロパティです。 以外にも、 **DataSourceID**と**ファイル**プロパティ、次のプロパティはそれぞれの使用可能な**場所**リモート パーティションを復元するための要素。  
  
-   指定されたリモート データ ソースの接続文字列を上書きする**DataSourceID**、設定することができます、 **ConnectionString**のプロパティ、**場所**要素を別の接続文字列。 **復元**コマンドに含まれている接続文字列を使用し、 **ConnectionString**プロパティです。 場合**ConnectionString**が指定されていない、**復元**コマンドは、指定されたリモート データ ソースのバックアップ ファイルに格納されている接続文字列を使用します。 使用することができます、 **ConnectionString**別のリモート インスタンスにリモート パーティションを移動するには設定します。 ただし、使用することはできません、 **ConnectionString**を復元したデータベースを含む同じインスタンスにリモート パーティションを復元するには設定します。 つまり、使用することはできません、 **ConnectionString**プロパティをローカル パーティションにリモート パーティションを作成します。  
  
-   リモート データ ソース上のリモート パーティションの格納に使用される各元フォルダーを指定できます、[フォルダー](../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)元のフォルダーに格納されているすべてのリモート パーティションを復元するための新しいフォルダーを示す要素。 場合、**フォルダー**要素が指定されていない、**復元**コマンドはリモート バックアップ ファイルに含まれているリモート パーティションに対して指定された元のフォルダーを使用します。  
  
### <a name="relocating-rolap-objects"></a>ROLAP オブジェクトの再配置  
 **復元**コマンドは、集計やなどの情報は、基になるリレーショナル データ ソースのテーブルに格納されるので、ROLAP ストレージを使用するオブジェクトのデータを復元できません。 ただし、ROLAP オブジェクトのメタデータは復元できます。 ROLAP オブジェクトのメタデータを復元する、**復元**コマンドは、リレーショナル データ ソースにテーブル構造を再作成します。  
  
 使用することができます、**場所**内の要素、**復元**ROLAP オブジェクトを再配置するコマンド。 各**場所**要素のデータ ソースを再配置するために使用、 **%datasourcetype**明示的にプロパティを設定する必要があります*ローカル*です。 設定する必要も、 **ConnectionString**のプロパティ、**場所**を新しい場所の接続文字列の要素。 復元中、**復元**コマンドには、によって識別されるデータ ソースの接続文字列が置き換えられます、 **DataSourceID**のプロパティ、**場所**要素値を持つ、 **ConnectionString**のプロパティ、**場所**要素。  
  
##  <a name="synchronizing_databases"></a>データベースの同期  
 **同期**コマンドの指定したメタデータやデータの同期[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]別のデータベースとデータベースです。 **同期**コマンドには、ソース データベースを指定することのできるさまざまなプロパティをセキュリティ定義、リモート パーティションを同期して、ROLAP オブジェクトの同期を同期する方法です。  
  
> [!NOTE]  
>  **同期**コマンドは、サーバー管理者とデータベース管理者によってのみ実行できます。 同期元データベースと同期先のデータベースの両方の互換性レベルが同じであることが必要です。  
  
### <a name="specifying-the-source-database"></a>同期元データベースの指定  
 [ソース](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)のプロパティ、**同期**コマンドには、2 つのプロパティが含まれています。 **ConnectionString**と**オブジェクト**です。 **ConnectionString**プロパティには、ソース データベースが格納されているインスタンスの接続文字列が含まれています。 および**オブジェクト**プロパティには、ソース データベースのオブジェクト識別子が含まれています。  
  
 移行先データベースでは、現在のデータベースがされるセッションでの**同期**コマンドを実行します。  
  
 場合、 **ApplyCompression**のプロパティ、**同期**コマンドが設定されているを true に、ソースから送信される情報は、転送先データベースにデータベースが送信される前に圧縮されています。  
  
### <a name="synchronizing-security-settings"></a>セキュリティ設定の同期  
 [SynchronizeSecurity](../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)プロパティを決定するかどうか、**同期**コマンドは、ロールや権限、ソース データベースで定義されているなど、セキュリティ定義を同期します。 **SynchronizeSecurity**プロパティも決定するかどうか、**同期**コマンドには、Windows ユーザー アカウントと、セキュリティ定義のメンバーとして定義されているグループが含まれています。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*SkipMembership*|同期先データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|同期先データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*Ignoresecurity のいずれか*|同期先データベースからセキュリティ定義を除外します。|  
  
### <a name="synchronizing-remote-partitions"></a>リモート パーティションの同期  
 ソース データベースに存在するリモート データ ソースごとに関連付けられている各リモート パーティションを同期を含めることによって、**場所**内の要素、**場所**のプロパティ、 **同期**コマンド。 各**場所**要素、 **%datasourcetype**プロパティを除外または明示的に設定する必要があります*リモート*です。  
  
 定義し、コピー先データベースにリモート データ ソースへの接続、**同期**コマンドで定義されている接続文字列を使用して、 **ConnectionString**のプロパティ、**場所**要素。 **同期**コマンドを使用し、 **DataSourceID**のプロパティ、**場所**要素を同期するためにリモート パーティションを識別します。 **同期**コマンドで指定されたリモート データ ソース上のリモート パーティションを同期する、 **DataSourceID**ソース データベース上で、で指定されたリモートデータソースのプロパティ**DataSourceID**転送先データベースのプロパティです。  
  
 ソース データベース上のリモート データ ソースのリモート パーティションを格納するために使用元フォルダーごとに指定することも、**フォルダー**内の要素、**場所**要素。 **フォルダー**要素は、リモート データ ソースの元のフォルダーに格納されているすべてのリモート パーティションを同期するための転送先データベースに新しいフォルダーを示します。 場合、**フォルダー**要素が指定されていない、Synchronize コマンドは、ソース データベースに含まれているリモート パーティションに対して指定された元のフォルダーを使用します。  
  
### <a name="synchronizing-rolap-objects"></a>ROLAP オブジェクトの同期  
 **同期**コマンドは、集計やなどの情報は、基になるリレーショナル データ ソースのテーブルに格納されるので、ROLAP ストレージを使用するオブジェクトのデータを同期できません。 ただし、ROLAP オブジェクトのメタデータは同期できます。 メタデータを同期するために、**同期**コマンドは、リレーショナル データ ソースにテーブル構造を再作成します。  
  
 使用することができます、**場所**ROLAP オブジェクトを同期する同期コマンド内の要素。 各**場所**要素のデータ ソースを再配置するために使用、 **%datasourcetype**明示的にプロパティを設定する必要があります*ローカル*です。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 設定する必要も、 **ConnectionString**のプロパティ、**場所**を新しい場所の接続文字列の要素。 同期中に、**同期**コマンドには、によって識別されるデータ ソースの接続文字列が置き換えられます、 **DataSourceID**のプロパティ、**場所**値を持つ要素、 **ConnectionString**のプロパティ、**場所**要素。  
  
## <a name="see-also"></a>参照  
 [Backup 要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [要素 &#40; を復元します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  

