---
title: CLR 統合のコードアクセスセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
ms.openlocfilehash: f49968392dd813b48f43e5e63586fd0c6bec71d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118517"
---
# <a name="clr-integration-code-access-security"></a>CLR 統合のコード アクセス セキュリティ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティというセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 詳細については、.NET Framework Software Development Kit の「コード アクセス セキュリティ」を参照してください。  
  
 アセンブリに許可される権限を決定するセキュリティ ポリシーは、次の 3 つに分類されます。  
  
-   コンピューター ポリシー : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がインストールされているコンピューターで実行されるすべてのマネージド コードに対して効力を持つポリシーです。  
  
-   ユーザー ポリシー : 特定のプロセスをホストとするマネージド コードに対して効力を持つポリシーです。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合、ユーザー ポリシーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを実行している Windows アカウントに対して固有になります。  
  
-   ホスト ポリシー : CLR のホスト (この場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) によって設定され、そのホストで実行されるマネージド コードに対して効力を持つポリシーです。  
  
 CLR でサポートされるコード アクセス セキュリティ メカニズムは、ランタイムが完全に信頼されるコードと部分的に信頼されるコードの両方をホストできるという前提に基づいています。 CLR コード アクセス セキュリティで保護されるリソースは、通常、そのリソースへのアクセスを許可する前に適切な権限を必要とするマネージド アプリケーション プログラミング インターフェイスによってラップされます。 権限の要求は、(アセンブリ レベルで) 呼び出し履歴内のすべての呼び出し側が、対応するリソース権限を持つ場合にのみ満たされます。  
  
 マネージド コードを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で実行する際に許可されるコード アクセス セキュリティ権限のセットは、上記の 3 つのポリシー レベルで許可される権限のセットの共通部分です。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込まれたアセンブリに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が一連の権限を許可しても、最終的にユーザー コードに許可される権限セットは、ユーザー レベルおよびコンピューター レベルのポリシーによってさらに制限されることがあります。  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>SQL Server ホスト ポリシー レベルの権限セット  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシー レベルでアセンブリに許可されるコード アクセス セキュリティ権限のセットは、アセンブリの作成時にどの権限セットを指定するかによって決定されます。 権限セットには、 **SAFE**、 **EXTERNAL_ACCESS** 、 **UNSAFE**の3つがあります ( [CREATE ASSEMBLY &#40;transact-sql&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)) の**PERMISSION_SET**オプションを使用して指定します。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、CLR のホスト時に、ホスト レベルのセキュリティ ポリシー レベルを提供します。このポリシーは、常に効力を持つ 2 つのポリシー レベルより下位の追加ポリシー レベルになります。 このポリシーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって作成されるアプリケーション ドメインごとに設定されます。 このポリシーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が CLR のインスタンスを作成するときに有効になる、既定のアプリケーション ドメイン用ではありません。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト レベル ポリシーは、システム アセンブリの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固定ポリシーと、ユーザー アセンブリのユーザー指定ポリシーの組み合わせです。  
  
 CLR アセンブリと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] システム アセンブリの固定ポリシーでは、これらのアセンブリを完全に信頼します。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、アセンブリの所有者がアセンブリごとに指定する 3 つの権限バケットのいずれかに基づきます。 次に示すセキュリティ権限の詳細については、.NET Framework SDK を参照してください。  
  
### <a name="safe"></a>SAFE  
 内部コンピューター処理とローカル データのアクセスだけが許可されます。 **SAFE**は最も制限の厳しい権限セットです。 **安全**なアクセス許可を持つアセンブリによって実行されるコードは、ファイル、ネットワーク、環境変数、レジストリなどの外部システムリソースにアクセスすることはできません。  
  
 **セーフ**アセンブリには、次のアクセス許可と値があります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**SecurityPermission**|**実行:** マネージコードを実行するためのアクセス許可。|  
|**System.data.sqlclient.sqlclientpermission**|**Context connection = true**、 **context connection = yes**: コンテキスト接続のみを使用できます。接続文字列には、"context connection = true" または "context connection = yes" の値のみを指定できます。<br /><br /> **Allow空白パスワード = false:** 空のパスワードは許可されていません。|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS アセンブリは**安全**なアセンブリと同じアクセス許可を持ち、ファイル、ネットワーク、環境変数、レジストリなどの外部システムリソースにアクセスする機能が追加されています。  
  
 **EXTERNAL_ACCESS**アセンブリには、次のアクセス許可と値もあります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**無制限:** 分散トランザクションは許可されます。|  
|**DNSPermission**|**無制限:** ドメインネームサーバーから情報を要求するアクセス許可。|  
|**環境権限**|**無制限:** システム環境変数とユーザー環境変数へのフルアクセスが許可されます。|  
|**EventLogPermission**|**管理:** イベントソースの作成、既存のログの読み取り、イベントソースまたはログの削除、エントリへの応答、イベントログの消去、イベントの待機、およびすべてのイベントログのコレクションへのアクセスが許可されます。|  
|**FileIOPermission**|**無制限:** ファイルとフォルダーへのフルアクセスが許可されます。|  
|**KeyContainerPermission**|**無制限:** キーコンテナーへのフルアクセスが許可されます。|  
|**NetworkInformationPermission**|**アクセス:** Ping は許可されています。|  
|**RegistryPermission**|**HKEY_CLASSES_ROOT**、 **HKEY_LOCAL_MACHINE**、 **HKEY_CURRENT_USER**、 **HKEY_CURRENT_CONFIG**、および HKEY_USERS に対する読み取り権限を許可**します。**|  
|**SecurityPermission**|**アサーション:** このコードのすべての呼び出し元が操作に必要なアクセス許可を持っていることをアサートする機能。<br /><br /> **Controlprincipal:** プリンシパルオブジェクトを操作する機能。<br /><br /> **実行:** マネージコードを実行するためのアクセス許可。<br /><br /> **Serializationformatter:** シリアル化サービスを提供する機能。|  
|**SmtpPermission**|**アクセス:** SMTP ホストポート25への発信接続は許可されています。|  
|**SocketPermission**|**接続:** トランスポートアドレスの送信接続 (すべてのポート、すべてのプロトコル) が許可されます。|  
|**System.data.sqlclient.sqlclientpermission**|**無制限:** データソースへのフルアクセスが許可されます。|  
|**StorePermission**|**無制限:** X.509 証明書ストアへのフルアクセスが許可されます。|  
|**WebPermission**|**接続:** Web リソースへの送信接続が許可されます。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE では、アセンブリから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外のリソースにも無制限にアクセスできます。 **UNSAFE**アセンブリ内からコードを実行すると、アンマネージコードを呼び出すこともできます。  
  
 **UNSAFE**アセンブリには**FullTrust**が指定されています。  
  
> [!IMPORTANT]  
>  **SAFE**は、の外部[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のリソースにアクセスせずに計算とデータ管理タスクを実行するアセンブリに推奨される権限設定です。 **** 外部[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のリソースにアクセスするアセンブリには EXTERNAL_ACCESS をお勧めします。 **EXTERNAL_ACCESS**アセンブリは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]既定でサービスアカウントとして実行されます。 **EXTERNAL_ACCESS**コードは、呼び出し元の Windows 認証セキュリティコンテキストを明示的に偽装することができます。 既定では[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスアカウントとして実行されるため、 **EXTERNAL_ACCESS**を実行するアクセス許可は、サービスアカウントとして実行するために信頼されているログインにのみ付与する必要があります。 セキュリティの観点からは、 **EXTERNAL_ACCESS**と**UNSAFE**アセンブリは同じです。 ただし、 **EXTERNAL_ACCESS**アセンブリは、**安全**でないアセンブリに含まれていないさまざまな信頼性および堅牢性保護を提供します。 **UNSAFE**を指定すると、アセンブリ内のコードは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]プロセス空間に対して無効な操作を実行できるため、の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]堅牢性とスケーラビリティを損なう可能性があります。 で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]clr アセンブリを作成する方法の詳細については、「 [clr 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)」を参照してください。  
  
## <a name="accessing-external-resources"></a>外部リソースへのアクセス  
 ユーザー定義型 (UDT)、ストアドプロシージャ、またはその他の種類のコンストラクトアセンブリが**安全**なアクセス許可セットに登録されている場合、そのコンストラクトで実行されるマネージコードは外部リソースにアクセスできません。 ただし、 **EXTERNAL_ACCESS**または**UNSAFE**アクセス許可セットが指定され、マネージコードが外部リソースにアクセスしよう[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]とすると、によって次の規則が適用されます。  
  
|状況|対処|  
|--------|----------|  
|実行コンテキストが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対応している場合。|外部リソースへのアクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していると同時に、本来の呼び出し元である場合。|外部リソースへのアクセスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストで行われます。|  
|呼び出し元が、本来の呼び出し元ではない場合。|アクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していて、実行コンテキストが本来の呼び出し元であり、呼び出し元の権限が借用されている場合。|アクセスにはサービス アカウントではなく、呼び出し元のセキュリティ コンテキストが使用されます。|  
  
## <a name="permission-set-summary"></a>権限セットの概要  
 次の表は、 **SAFE**、 **EXTERNAL_ACCESS**、および**UNSAFE**アクセス許可セットに付与される制限とアクセス許可をまとめたものです。  
  
|||||  
|-|-|-|-|  
||**セーフ**|**EXTERNAL_ACCESS**|**UNSAFE**|  
|**コードアクセスセキュリティのアクセス許可**|実行のみ|実行および外部リソースへのアクセス|無制限 (P/Invoke を含む)|  
|**プログラミング モデルの制限事項**|はい|はい|制限なし|  
|**検証可能性の要件**|はい|はい|いいえ|  
|**ローカルデータアクセス**|はい|はい|はい|  
|**ネイティブ コードを呼び出す機能**|いいえ|いいえ|はい|  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 統合プログラミングモデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR ホスト環境](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
