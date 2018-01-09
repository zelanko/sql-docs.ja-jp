---
title: "アセンブリを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 249bd52e59dfb91ca4d4a24efb3cd824fb329864
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="creating-an-assembly"></a>アセンブリを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]ストアド プロシージャやトリガーなどのマネージ データベース オブジェクトはコンパイルされ、アセンブリと呼ばれる単位で配置されます。 マネージ DLL アセンブリを登録する必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アセンブリが提供する機能を使用する前にします。 アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録するには、CREATE ASSEMBLY ステートメントを使用します。 ここでは、CREATE ASSEMBLY ステートメントを使用してアセンブリをデータベースに登録する方法と、アセンブリのセキュリティ設定を指定する方法について説明します。  
  
## <a name="the-create-assembly-statement"></a>CREATE ASSEMBLY ステートメント  
 データベースにアセンブリを作成するには、CREATE ASSEMBLY ステートメントを使用します。 次に例を示します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 FROM 句では、作成するアセンブリのパス名を指定します。 このパスには、UNC (汎用名前付け規則) パスか、コンピューターにローカルの物理ファイル パスを指定できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、名前、カルチャ、および公開キーが同じでありバージョンが異なるアセンブリの登録を許可していません。  
  
 他のアセンブリを参照するアセンブリを作成することもできます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にアセンブリを作成するときに、ルートレベルのアセンブリによって参照されるアセンブリがデータベースにまだ作成されていない場合は、そのアセンブリが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって作成されます。  
  
 データベース ユーザーまたはユーザー ロールには、データベースにアセンブリを作成して所有する権限が与えられます。 アセンブリを作成するには、データベース ユーザーまたはロールに CREATE ASSEMBLY 権限が許可されている必要があります。  
  
 アセンブリから他のアセンブリを参照できる条件を次に示します。  
  
-   呼び出し先または参照先のアセンブリが同じユーザーまたはロールによって所有されている。  
  
-   呼び出し先または参照先のアセンブリが同じデータベースに作成されている。  
  
## <a name="specifying-security-when-creating-assemblies"></a>アセンブリ作成時のセキュリティの指定  
 アセンブリを作成するときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース、ことを指定するコードを実行できるセキュリティの 3 つの異なるレベルのいずれかの:**セーフ**、 **EXTERNAL_ACCESS**、または**UNSAFE**. ときに、 **CREATE ASSEMBLY**ステートメントを実行するサーバーの登録に失敗するアセンブリを引き起こす可能性がありますコード アセンブリに対して特定チェックを実行します。 詳細については、の Impersonation サンプルを参照してください。 [CodePlex](http://msftengprodsamples.codeplex.com/)です。  
  
 **安全な**は既定の権限セットと、ほとんどのシナリオで機能します。 特定のセキュリティ レベルを指定するには、CREATE ASSEMBLY ステートメントの構文を次のように変更します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 アセンブリを作成することも、**セーフ**単に上記のコードの 3 行目を省略すると、アクセス許可セットします。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 アセンブリのコードを実行するときに、**セーフ**アクセス許可を設定することのみを実行できます演算とインプロセス マネージ プロバイダーを使用してサーバー内のデータ アクセスします。  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>EXTERNAL_ACCESS および UNSAFE アセンブリの作成  
 **EXTERNAL_ACCESS**ファイル、ネットワーク、レジストリ、および環境変数など、サーバーの外部のリソースにアクセスするコードが必要なシナリオに対処します。 サーバーから外部リソースにアクセスする場合、常にマネージ コードの呼び出し元のユーザーのセキュリティ コンテキストが借用されます。  
  
 **安全でない**状況アセンブリが検証可能な安全ではないまたはへの追加アクセスが必要ですが、リソースをなど制限付きコード権限は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API です。  
  
 作成する、 **EXTERNAL_ACCESS**または**UNSAFE**内のアセンブリ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、次の 2 つの条件のいずれかが満たす必要があります。  
  
1.  アセンブリが、厳密な名前で署名されているか、または証明書を使用して Authenticode で署名されている。 内でこの厳密な名前 (または証明書) が作成された[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]非対称キー (または証明書) として、対応するログインは、 **EXTERNAL ACCESS ASSEMBLY**権限 (外部アクセス アセンブリの場合) に対してまたは**UNSAFE アセンブリ**権限 (に対して安全でないアセンブリの場合)。  
  
2.  データベースの所有者 (DBO) は**EXTERNAL ACCESS ASSEMBLY** (の**外部アクセス**アセンブリ) または**UNSAFE ASSEMBLY** (の**UNSAFE**アセンブリの場合) のアクセス許可、およびデータベースが、 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)'éý' **ON**です。  
  
 上に示した 2 つの条件は、アセンブリの読み込み時 (実行も含む) にもチェックされます。 アセンブリを読み込むには、これらの条件の少なくとも 1 つが満たされている必要があります。  
  
 お勧め、 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)データベースでないに設定されている**ON**ランタイム (CLR) が、サーバー プロセス内のコードに共通の言語を実行するだけです。 代わりに、master データベースのアセンブリ ファイルから非対称キーを作成してください。 この非対称キーにマップされるログインを作成し、必要があります、およびそのログインを許可する必要があります**EXTERNAL ACCESS ASSEMBLY**または**UNSAFE ASSEMBLY**権限です。  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントは、非対称キーを作成にこのキーは、ログインをマップし、付与するために必要な手順を実行します**EXTERNAL_ACCESS**権限をログインします。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  非対称キーに関連付ける新しいログインを作成する必要があります。 このログインは、権限を許可するためにのみ使用します。このログインをユーザーに関連付けたり、アプリケーション内で使用したりする必要はありません。  
  
 作成する、**外部アクセス**のにアセンブリ、作成者が必要な**外部アクセス**権限です。 この権限は、アセンブリの作成時に次のように指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントは、非対称キーを作成にこのキーは、ログインをマップし、付与するために必要な手順を実行します**UNSAFE**権限をログインします。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 アセンブリを読み込むことを指定する**UNSAFE** 、アクセス許可を指定する、 **UNSAFE**アクセス許可が、サーバーにアセンブリを読み込む場合の設定。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 各設定のアクセス許可の詳細については、次を参照してください。 [CLR 統合のセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)です。  
  
## <a name="see-also"></a>参照  
 [CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [アセンブリを変更します。](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [アセンブリを削除します。](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)   
 [呼び出し元が信頼されている部分的に許可します。](http://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
