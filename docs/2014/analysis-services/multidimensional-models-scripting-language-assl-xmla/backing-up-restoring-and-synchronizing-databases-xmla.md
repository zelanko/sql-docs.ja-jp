---
title: データベースのバックアップ、復元、および同期 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- restoring databases [XML for Analysis]
- backing up databases [XML for Analysis]
- database backups [XML for Analysis]
- synchronization [XML for Analysis]
- database restores [XML for Analysis]
ms.assetid: 6c021b2e-6ad0-444e-b23f-4b5f72ce084b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 500435a585ffed84a8f16e2b3bd1c4db14509103
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545084"
---
# <a name="backing-up-restoring-and-synchronizing-databases-xmla"></a>データベースのバックアップ、復元、および同期 (XMLA)
  XML for Analysis には、データベースのバックアップ、復元、および同期を行う 3 つのコマンドがあります。  
  
-   [Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)コマンドは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 「[データベース](#backing_up_databases)のバックアップ」で説明されているように、バックアップファイル (abf) を使用してデータベースをバックアップします。  
  
-   [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)コマンドは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 「データベースの[復元](#restoring_databases)」セクションで説明されているように、abf ファイルからデータベースを復元します。  
  
-   [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)コマンドは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 「[データベースの同期](#synchronizing_databases)」で説明されているように、1つのデータベースを別のデータベースのデータおよびメタデータと同期します。  
  
##  <a name="backing-up-databases"></a><a name="backing_up_databases"></a>データベースのバックアップ  
 上で述べたように、`Backup` コマンドは指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをバックアップ ファイルにバックアップします。 `Backup` コマンドには、バックアップするデータベースや使用するバックアップ ファイル、セキュリティ定義のバックアップ方法、およびバックアップするリモート パーティションを指定するためのさまざまなプロパティがあります。  
  
> [!IMPORTANT]  
>  Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。 また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 バックアップするデータベースを指定するには、コマンドの[オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティを設定し `Backup` ます。 `Object` プロパティには、データベースを表すオブジェクト識別子を含める必要があります。含まれていない場合、エラーが発生します。  
  
 バックアッププロセスによって作成および使用されるファイルを指定するには、コマンドの[file](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/file-element-xmla)プロパティを設定し `Backup` ます。 `File` プロパティは、作成するバックアップ ファイルの UNC パスとファイル名に設定する必要があります。  
  
 バックアップに使用するファイルの指定に加えて、指定したバックアップ ファイルに対する以下のオプションを設定できます。  
  
-   [Allowoverwrite](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/allowoverwrite-element-xmla)プロパティを true に設定すると、指定した `Backup` ファイルが既に存在する場合、コマンドによってバックアップファイルが上書きされます。 `AllowOverwrite` プロパティを false に設定した場合、指定されたバックアップ ファイルが既に存在すると、エラーが発生します。  
  
-   [Applycompression](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/applycompression-element-xmla)プロパティを true に設定すると、ファイルの作成後にバックアップファイルが圧縮されます。  
  
-   [Password](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/password-element-xmla)プロパティを空白以外の値に設定すると、指定したパスワードを使用してバックアップファイルが暗号化されます。  
  
    > [!IMPORTANT]  
    >  `ApplyCompression` および `Password` プロパティが指定されない場合、バックアップ ファイルには接続文字列に含まれるユーザー名とパスワードがクリア テキストで格納されます。 クリア テキストで格納されたデータは、取得される可能性があります。 セキュリティを強化するためには、`ApplyCompression` および `Password` 設定を使用して、バックアップの圧縮と暗号化の両方を行ってください。  
  
### <a name="backing-up-security-settings"></a>セキュリティ設定のバックアップ  
 [セキュリティ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)プロパティは、 `Backup` データベースで定義されているロールや権限などのセキュリティ定義をコマンドがバックアップするかどうかを決定し [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 `Security` プロパティは、バックアップ ファイルに、セキュリティ定義のメンバーとして Windows ユーザー アカウントとグループを含めるかどうかも決定します。  
  
 `Security` プロパティの値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*SkipMembership*|バックアップ ファイルにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|バックアップ ファイルにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|バックアップ ファイルからセキュリティ定義を除外します。|  
  
### <a name="backing-up-remote-partitions"></a>リモート パーティションのバックアップ  
 データベース内のリモートパーティションをバックアップするには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コマンドの[Backupremotepartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/backupremotepartitions-element-xmla)プロパティを `Backup` true に設定します。 この設定を行うと、`Backup` コマンドは、データベースのリモート パーティションを格納するために使用するリモート バックアップ ファイルを、各リモート データ ソースに対して作成します。  
  
 バックアップする各リモートデータソースについて、コマンドの Location[プロパティに](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/locations-element-xmla) [Location](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/location-element-xmla)要素を含めることによって、対応するバックアップファイルを指定でき `Backup` ます。 `Location`要素のプロパティは、 `File` リモートバックアップファイルの UNC パスとファイル名に設定し、その[DataSourceID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)プロパティには、データベースで定義されているリモートデータソースの識別子を設定する必要があります。  
  
##  <a name="restoring-databases"></a><a name="restoring_databases"></a>復元 (データベースを)  
 `Restore` コマンドは、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをバックアップ ファイルから復元します。 `Restore` コマンドには、復元するデータベースや使用するバックアップ ファイル、セキュリティ定義の復元方法、復元するリモート パーティション、およびリレーショナル OLAP (ROLAP) オブジェクトの再配置を指定するためのさまざまなプロパティがあります。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 データベースを上書きするには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ユーザーは、インスタンスのサーバーロールのメンバーである [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] か、または復元するデータベースに対してフルコントロール (管理者) 権限を持つデータベースロールのメンバーである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
### <a name="specifying-the-database-and-backup-file"></a>データベースとバックアップ ファイルの指定  
 `DatabaseName` コマンドの `Restore` プロパティには、データベースを表すオブジェクト識別子を含める必要があります。含まれていない場合、エラーが発生します。 指定されたデータベースが既に存在する場合、既存のデータベースを上書きするかどうかは、`AllowOverwrite` プロパティによって決定されます。 `AllowOverwrite` プロパティが false に設定されている場合、指定されたデータベースが既に存在すると、エラーが発生します。  
  
 `File` コマンドの `Restore` プロパティは、指定されたデータベースに復元するバックアップ ファイルの UNC パスとファイル名に設定する必要があります。 指定されたバックアップ ファイルに対して `Password` プロパティを設定することもできます。 `Password` プロパティを空白以外の任意の値に設定すると、指定されたパスワードを使用してバックアップ ファイルが暗号化解除されます。 バックアップ ファイルが暗号化されていない場合、または指定されたパスワードがバックアップ ファイルの暗号化に使用されたパスワードと一致しない場合は、エラーが発生します。  
  
### <a name="restoring-security-settings"></a>セキュリティ設定の復元  
 `Security` プロパティは、ロールや権限などの、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースで定義されているセキュリティ定義を `Restore` コマンドが復元するかどうかを決定します。 `Security` プロパティは、`Restore` コマンドが復元プロセスの一部として、Windows ユーザー アカウントとグループをセキュリティ定義のメンバーに含めるかどうかも決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*SkipMembership*|データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|データベースからセキュリティ定義を除外します。|  
  
### <a name="restoring-remote-partitions"></a>リモート パーティションの復元  
 以前の `Backup` コマンドの実行時に作成された各リモート バックアップ ファイルについては、`Location` コマンドの `Locations` プロパティに `Restore` 要素を含めることによって、それに関連付けられているリモート パーティションを復元することができます。 各要素の[DataSourceType](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)プロパティは、 `Location` 除外するか、明示的に*Remote*に設定する必要があります。  
  
 指定された各 `Location` 要素に関して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、`DataSourceID` プロパティで指定されたリモート データ ソースにアクセスし、`File` プロパティで指定されたリモート バックアップ ファイルで定義されているパーティションを復元します。 `DataSourceID` および `File` プロパティに加えて、リモート パーティションを復元するために使用される各 `Location` 要素では、以下のプロパティを使用できます。  
  
-   `DataSourceID` 要素の `ConnectionString` プロパティを別の接続文字列に設定すると、`Location` で指定されたリモート データ ソースへの接続文字列をオーバーライドできます。 その場合、`Restore` コマンドは、`ConnectionString` プロパティに含まれる接続文字列を使用します。 `ConnectionString` が指定されていない場合、`Restore` コマンドは、指定されたリモート データ ソースのバックアップ ファイルに格納されている接続文字列を使用します。 `ConnectionString` 設定を使用すると、リモート パーティションを別のリモート インスタンスに移動することができます。 ただし、`ConnectionString` 設定を使用して、復元されるデータベースを含む同じインスタンスにリモート パーティションを復元することはできません。 つまり、`ConnectionString` プロパティを使用してリモート パーティションをローカル パーティションにすることはできません。  
  
-   リモートデータソースにリモートパーティションを格納するために使用する元のフォルダーごとに、[フォルダー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/folder-element-xmla)要素を指定して、元のフォルダーに格納されているすべてのリモートパーティションを復元する新しいフォルダーを指定できます。 `Folder` 要素が指定されていない場合、`Restore` コマンドは、リモート バックアップ ファイルに含まれるリモート パーティションに対して指定されている元のフォルダーを使用します。  
  
### <a name="relocating-rolap-objects"></a>ROLAP オブジェクトの再配置  
 `Restore` コマンドでは、ROLAP ストレージを使用するオブジェクトの集計やデータを復元できません。そのような情報は、基になるリレーショナル データ ソースのテーブルに格納されているためです。 ただし、ROLAP オブジェクトのメタデータは復元できます。 ROLAP オブジェクトのメタデータを復元するために、`Restore` コマンドはリレーショナル データ ソースのテーブル構造を再作成します。  
  
 `Location` コマンドで `Restore` 要素を使用すると、ROLAP オブジェクトの再配置を行えます。 `Location`データソースの再配置に使用される要素ごとに、 `DataSourceType` プロパティを明示的に*Local*に設定する必要があります。 また、`ConnectionString` 要素の `Location` プロパティを、新しい場所の接続文字列に設定する必要があります。 復元の実行時に、`Restore` コマンドは、`DataSourceID` 要素の `Location` プロパティによって識別されるデータ ソースへの接続文字列を、`ConnectionString` 要素の `Location` プロパティの値に置き換えます。  
  
##  <a name="synchronizing-databases"></a><a name="synchronizing_databases"></a>データベースの同期  
 `Synchronize` コマンドは、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのデータとメタデータを別のデータベースと同期させます。 `Synchronize` コマンドには、同期元データベースやセキュリティ定義の同期方法、同期するリモート パーティション、および ROLAP オブジェクトの同期を指定するためのさまざまなプロパティがあります。  
  
> [!NOTE]  
>  `Synchronize` コマンドを実行できるのは、サーバー管理者とデータベース管理者だけです。 同期元データベースと同期先のデータベースの両方の互換性レベルが同じであることが必要です。  
  
### <a name="specifying-the-source-database"></a>同期元データベースの指定  
 コマンドの[Source](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティには `Synchronize` 、とという2つのプロパティが含まれてい `ConnectionString` `Object` ます。 `ConnectionString` プロパティには同期元データベースを含むインスタンスの接続文字列が含まれ、`Object` プロパティには同期元データベースのオブジェクト識別子が含まれます。  
  
 同期先データベースは、`Synchronize` コマンドが実行されるセッションでの現在のデータベースです。  
  
 `ApplyCompression` コマンドの `Synchronize` プロパティが true に設定されている場合、同期元データベースから同期先データベースへ送信される情報は、送信前に圧縮されます。  
  
### <a name="synchronizing-security-settings"></a>セキュリティ設定の同期  
 [SynchronizeSecurity](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/security-element-xmla)プロパティは、 `Synchronize` ソースデータベースで定義されているセキュリティ定義 (ロールや権限など) をコマンドが同期するかどうかを決定します。 `SynchronizeSecurity` プロパティは、`Sychronize` コマンドが Windows ユーザー アカウントとグループをセキュリティ定義のメンバーに含めるかどうかも決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*SkipMembership*|同期先データベースにセキュリティ定義を含めますが、メンバーシップ情報は除外します。|  
|*CopyAll*|同期先データベースにセキュリティ定義とメンバーシップ情報を含めます。|  
|*IgnoreSecurity*|同期先データベースからセキュリティ定義を除外します。|  
  
### <a name="synchronizing-remote-partitions"></a>リモート パーティションの同期  
 同期元データベース上に存在する各リモート データ ソースについては、`Location` コマンドの `Locations` プロパティに `Synchronize` 要素を含めることによって、それぞれに関連付けられているリモート パーティションを同期させることができます。 要素ごとに `Location` 、 `DataSourceType` プロパティを除外するか、明示的に*Remote*に設定する必要があります。  
  
 同期先データベースのリモート データ ソースを定義してそれに接続するために、`Synchronize` コマンドでは、`ConnectionString` 要素の `Location` プロパティで定義されている接続文字列を使用します。 `Synchronize` コマンドはその後、`DataSourceID` 要素の `Location` プロパティを使用して、同期させるリモート パーティションを識別します。 この `Synchronize` コマンドは、ソースデータベースのプロパティで指定されたリモートデータソースのリモートパーティションを、 `DataSourceID` 転送先データベースのプロパティに指定されたリモートデータソースと同期し `DataSourceID` ます。  
  
 同期先データベースのリモート データ ソース上のリモート パーティションを格納するために使用されている元の各フォルダーについて、`Folder` 要素に `Location` 要素を指定することもできます。 `Folder` 要素は、リモート データ ソース上の元のフォルダーに格納されているすべてのリモート パーティションを同期させるための、同期先データベースに対する新しいフォルダーを示します。 `Folder` 要素が指定されていない場合、Synchronize コマンドは、同期元データベースに含まれるリモート パーティションに対して指定されている元のフォルダーを使用します。  
  
### <a name="synchronizing-rolap-objects"></a>ROLAP オブジェクトの同期  
 `Synchronize` コマンドでは、ROLAP ストレージを使用するオブジェクトの集計やデータを同期できません。そのような情報は、基になるリレーショナル データ ソースのテーブルに格納されているためです。 ただし、ROLAP オブジェクトのメタデータは同期できます。 メタデータを同期させるために、`Synchronize` コマンドはリレーショナル データ ソースのテーブル構造を再作成します。  
  
 Synchronize コマンドで `Location` 要素を使用すると、ROLAP オブジェクトの同期を行えます。 `Location`データソースの再配置に使用される要素ごとに、 `DataSourceType` プロパティを明示的に*Local*に設定する必要があります。 . また、`ConnectionString` 要素の `Location` プロパティを、新しい場所の接続文字列に設定する必要があります。 同期の実行時に、`Synchronize` コマンドは、`DataSourceID` 要素の `Location` プロパティによって識別されるデータ ソースへの接続文字列を、`ConnectionString` 要素の `Location` プロパティの値に置き換えます。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;Backup 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [XMLA&#41;&#40;Restore 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)   
 [XMLA&#41;&#40;要素の同期](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)   
 [Analysis Services データベースのバックアップと復元](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
