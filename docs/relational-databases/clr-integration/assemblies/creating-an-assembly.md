---
title: アセンブリの作成 |マイクロソフトドキュメント
description: アセンブリの作成を使用して、SQL Server にアセンブリを登録し、そのセキュリティ設定を指定します。 アセンブリを登録して、その機能を使用します。
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
ms.openlocfilehash: 6ca6787abae22722a7bbb99d335e63d47051bb46
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486839"
---
# <a name="creating-an-assembly"></a>アセンブリの作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ストアド プロシージャやトリガーなどのマネージド データベース オブジェクトは、コンパイルされた後、アセンブリと呼ばれる単位で配置されます。 マネージ DLL アセンブリは、アセンブリ[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]が提供する機能を使用する前に登録する必要があります。 アセンブリを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに登録するには、CREATE ASSEMBLY ステートメントを使用します。 ここでは、CREATE ASSEMBLY ステートメントを使用してアセンブリをデータベースに登録する方法と、アセンブリのセキュリティ設定を指定する方法について説明します。  
  
## <a name="the-create-assembly-statement"></a>アセンブリの作成ステートメント  
 データベースにアセンブリを作成するには、CREATE ASSEMBLY ステートメントを使用します。 たとえば次のようになります。  
  
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
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベースにアセンブリを作成する場合、コードを実行できる 3 つの異なるセキュリティ レベル **(SAFE** **、EXTERNAL_ACCESS、** または**UNSAFE)** のいずれかを指定できます。 CREATE **ASSEMBLY**ステートメントを実行すると、特定のチェックがコード アセンブリで実行され、サーバーへのアセンブリの登録に失敗する可能性があります。 詳細については、 [CodePlex](https://msftengprodsamples.codeplex.com/)の偽装サンプルを参照してください。  
  
 **SAFE**は既定のアクセス許可セットであり、ほとんどのシナリオで機能します。 特定のセキュリティ レベルを指定するには、CREATE ASSEMBLY ステートメントの構文を次のように変更します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 上記のコードの 3 行目を省略するだけで **、SAFE**アクセス許可セットを持つアセンブリを作成することもできます。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 アセンブリ内のコードが**SAFE**アクセス許可セットの下で実行される場合、インプロセスのマネージ プロバイダーを通じてサーバー内で計算とデータ アクセスのみを実行できます。  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>EXTERNAL_ACCESS および UNSAFE アセンブリの作成  
 **EXTERNAL_ACCESSは**、ファイル、ネットワーク、レジストリ、環境変数など、サーバーの外部のリソースにコードがアクセスする必要があるシナリオを示します。 サーバーから外部リソースにアクセスする場合、常にマネージド コードの呼び出し元のユーザーのセキュリティ コンテキストが借用されます。  
  
 **UNSAFE**コードのアクセス許可は、アセンブリが検証可能なほど安全でない場合や、Win32 API などの制限されたリソースへの[!INCLUDE[msCoName](../../../includes/msconame-md.md)]追加アクセスが必要な場合に使用されます。  
  
 **で EXTERNAL_ACCESS**または**UNSAFE** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アセンブリを作成するには、次の 2 つの条件のいずれかを満たす必要があります。  
  
1.  アセンブリが、厳密な名前で署名されているか、または証明書を使用して Authenticode で署名されている。 この厳密な名前 (または証明書)[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]は、非対称キー (または証明書) として内部に作成され、**外部アクセス アセンブリ**のアクセス許可 (外部アクセス アセンブリの場合) または**UNSAFE ASSEMBLY**アクセス許可 (安全でないアセンブリの場合) を持つ対応するログインがあります。  
  
2.  データベース所有者 (DBO)**には、外部アクセス アセンブリ**(**外部アクセス**アセンブリの場合) または**UNSAFE アセンブリ** **(UNSAFE**アセンブリの場合) のアクセス許可があり、データベースの[信頼できるデータベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)が**ON**に設定されています。  

 上に示した 2 つの条件は、アセンブリの読み込み時 (実行も含む) にもチェックされます。 アセンブリを読み込むには、これらの条件の少なくとも 1 つが満たされている必要があります。  
  
 サーバー プロセスで共通言語ランタイム (CLR) コードを実行する場合にのみ、データベースの[TRUSTWORTHY データベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)を**ON に**設定しないことをお勧めします。 代わりに、master データベースのアセンブリ ファイルから非対称キーを作成してください。 この非対称キーにマップされたログインを作成し、**外部アクセス アセンブリ**または**UNSAFE ASSEMBLY**アクセス許可をログインに付与する必要があります。  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]のステートメントは、非対称キーを作成し、ログインをこのキーにマップし、ログイン**にアクセス許可EXTERNAL_ACCESS**与えるために必要な手順を実行します。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
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
  
 **外部アクセス**アセンブリを作成するには、作成者に**外部アクセス**許可が必要です。 この権限は、アセンブリの作成時に次のように指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 次[!INCLUDE[tsql](../../../includes/tsql-md.md)]のステートメントは、非対称キーを作成し、ログインをこのキーにマップし、ログインに**UNSAFE**アクセス許可を付与するために必要な手順を実行します。 次に示す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントは、CREATE ASSEMBLY ステートメントを実行する前に実行する必要があります。  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 **UNSAFE**アクセス許可を持つアセンブリを読み込むには、アセンブリをサーバーに読み込むときに**UNSAFE**アクセス許可セットを指定します。  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 各設定のアクセス許可の詳細については、「 [CLR 統合セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [アセンブリの変更](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [アセンブリを削除する](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [CLR 統合コード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [信頼できるデータベース プロパティ](../../../relational-databases/security/trustworthy-database-property.md)   
 [部分的に信頼される呼び出し元の許容](https://msdn.microsoft.com/library/20b0248f-36da-4fc3-97d2-3789fcf6e084)  
  
  
