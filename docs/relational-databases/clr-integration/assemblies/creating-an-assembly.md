---
title: アセンブリを作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c9b69fa2c6ed790a33da50c0002b17a7e4461d0e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656761"
---
# <a name="creating-an-assembly"></a>アセンブリの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ストアド プロシージャやトリガーなどのマネージド データベース オブジェクトは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。 マネージ DLL アセンブリを登録する必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アセンブリが提供する機能を使用する前にします。 アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録するには、CREATE ASSEMBLY ステートメントを使用します。 ここでは、CREATE ASSEMBLY ステートメントを使用してアセンブリをデータベースに登録する方法と、アセンブリのセキュリティ設定を指定する方法について説明します。  
  
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
 アセンブリを作成するときに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、データベースを指定できます、コードが実行できるセキュリティの 3 つの異なるレベルのいずれか:**セーフ**、 **EXTERNAL_ACCESS**、または**UNSAFE**. ときに、 **CREATE ASSEMBLY**ステートメントを実行すると、サーバーの登録に失敗するアセンブリを引き起こす可能性のあるコード アセンブリで特定のチェックを実行します。 詳細については、の Impersonation サンプルを参照してください。 [CodePlex](https://msftengprodsamples.codeplex.com/)します。  
  
 **安全な**は、既定の権限セットと、ほとんどのシナリオで機能します。 特定のセキュリティ レベルを指定するには、CREATE ASSEMBLY ステートメントの構文を次のように変更します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 アセンブリを作成することも、**セーフ**上記のコードの 3 行目を省略するだけでアクセス許可セットします。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 アセンブリのコードを実行すると、**セーフ**アクセス許可設定のみを実行できます計算と、インプロセス マネージ プロバイダーを使用してサーバー内のデータ アクセス。  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>EXTERNAL_ACCESS および UNSAFE アセンブリの作成  
 **EXTERNAL_ACCESS**ファイル、ネットワーク、レジストリ、および環境変数など、サーバーの外部リソースにアクセスするコードが必要なシナリオに対処します。 サーバーから外部リソースにアクセスする場合、常にマネージド コードの呼び出し元のユーザーのセキュリティ コンテキストが借用されます。  
  
 **安全でない**など、アセンブリが検証可能な安全ではありませんまたはへの追加アクセスが必要です。 そのような状況に、リソースが制限されているコード権限は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 API です。  
  
 作成する、 **EXTERNAL_ACCESS**または**UNSAFE**でアセンブリ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、次の 2 つの条件のいずれかを満たす必要があります。  
  
1.  アセンブリが、厳密な名前で署名されているか、または証明書を使用して Authenticode で署名されている。 この厳密な名前 (または証明書) 内に作成[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]非対称キー (または証明書) として、対応するログインを使用して**EXTERNAL ACCESS ASSEMBLY** (外部アクセス アセンブリ) のアクセス許可または**UNSAFE ASSEMBLY** (unsafe アセンブリ) のアクセスを許可します。  
  
2.  データベース所有者 (DBO) が**EXTERNAL ACCESS ASSEMBLY** (の**外部アクセス**アセンブリ) または**UNSAFE ASSEMBLY** (の**UNSAFE**アセンブリの場合) のアクセス許可、およびデータベースが、 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)設定**ON**します。  
  
 上に示した 2 つの条件は、アセンブリの読み込み時 (実行も含む) にもチェックされます。 アセンブリを読み込むには、これらの条件の少なくとも 1 つが満たされている必要があります。  
  
 お勧め、 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)データベースでないに設定する**ON**ランタイム (CLR) がサーバー プロセス内のコードに共通の言語を実行するだけです。 代わりに、master データベースのアセンブリ ファイルから非対称キーを作成してください。 この非対称キーにマップされるログインを作成し、必要があります、およびログインを許可する必要があります**EXTERNAL ACCESS ASSEMBLY**または**UNSAFE ASSEMBLY**権限。  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントには、非対称キーを作成、このキーに、ログインをマップおよび許可し、必要な手順を実行する**EXTERNAL_ACCESS**権限をログインします。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
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
  
 作成する、**外部アクセス**は、アセンブリの作成者は、必要**外部アクセス**権限。 この権限は、アセンブリの作成時に次のように指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメントには、非対称キーを作成、このキーに、ログインをマップおよび許可し、必要な手順を実行する**UNSAFE**権限をログインします。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 アセンブリが読み込まれることを指定する**UNSAFE** 、アクセス許可を指定する、 **UNSAFE**のアクセス許可、サーバーにアセンブリを読み込むときの設定。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 各設定のアクセス許可の詳細については、[CLR 統合セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [アセンブリの変更](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [アセンブリの削除](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [CLR 統合のコード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)   
 [部分的に信頼される呼び出し元の許容](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
