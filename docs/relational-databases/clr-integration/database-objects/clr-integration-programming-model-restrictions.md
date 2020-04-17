---
title: CLR 統合プログラミング モデルの制限 |マイクロソフトドキュメント
description: SQL Server は、マネージ データベース オブジェクトが CREATE ASSEMBLY を使用して、実行時に最初に登録されたときに、マネージ データベース オブジェクトに対してコード チェックを実行します。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
ms.openlocfilehash: 83b73909cf1844796640a83910ee609eadd7dba4
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488544"
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 統合プログラミング モデルの制限事項
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  マネージ ストアド プロシージャやその他のマネージ データベース オブジェクトを構築する場合、そのことを考慮[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]する必要がある特定のコード チェックが実行されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**は、データベース**に最初に登録されたとき、CREATE ASSEMBLY ステートメントを使用して、および実行時にマネージ コード アセンブリのチェックを実行します。 マネージド コードが実行時にもチェックされるのは、実行時に決して到達しないコード パスがアセンブリに含まれる場合があるためです。  このチェックにより、サード パーティ アセンブリを柔軟に登録できます。特に、クライアント環境での実行を目的に作成され、ホストされた CLR では実行されない "安全でない" コードを含むアセンブリをブロックしないようにすることができるため、サード パーティ アセンブリに柔軟に対応できます。 マネージ コードが満たす必要がある要件は、アセンブリが**SAFE** **、EXTERNAL_ACCESS**、**または UNSAFE**、最も厳密な**UNSAFE**として登録されているかどうかによって異なります。  
  
 マネージド コード アセンブリには、制限事項に加えてコード セキュリティ権限も付与されます。 共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティ (CAS) というセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 **安全** **、EXTERNAL_ACCESS、****および安全でない**アセンブリには、異なる CAS アクセス許可があります。 詳細については、「 [CLR 統合コード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)」を参照してください。  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY チェック  
 CREATE **ASSEMBLY**ステートメントを実行すると、セキュリティ レベルごとに次のチェックが実行されます。  いずれかのチェックが失敗すると **、CREATE ASSEMBLY**はエラー メッセージで失敗します。  
  
### <a name="global-any-security-level"></a>グローバル (すべてのセキュリティ レベル)  
 参照されるすべてのアセンブリは、次の条件のうち 1 つ以上を満たす必要があります。  
  
-   既にデータベースに登録されていること。  
  
-   サポートされているアセンブリの 1 つであること。 詳細については、「[サポートされる .NET Framework ライブラリ](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
-   **CREATE ASSEMBLY FROM**_\<ロケーション>_ を使用しており、参照されているすべてのアセンブリとその依存関係は*\<、>の場所*で使用できます。  
  
-   **CREATE ASSEMBLY FROM**_\<バイト ..>_ を使用しており、すべての参照はスペース区切りのバイトを介して指定されます。  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 すべての**EXTERNAL_ACCESS**アセンブリは、次の条件を満たす必要があります。  
  
-   静的フィールドが情報の格納に使用されていないこと。 読み取り専用の静的フィールドは許可されます。  
  
-   PEVerify テストにパスしていること。 .NET Framework SDK には、MSIL コードと関連メタデータがタイプ セーフの要件を満たしていることをチェックするための PEVerify ツール (peverify.exe) が付属しています。  
  
-   同期は、**たとえば、同期属性**クラスでは使用されません。  
  
-   ファイナライザー メソッドが使用されていないこと。  
  
 次のカスタム属性は **、EXTERNAL_ACCESS**アセンブリでは許可されません。  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   アセンブリ**条件EXTERNAL_ACCESS**チェックされます。  
  
## <a name="runtime-checks"></a>ランタイム チェック  
 コード アセンブリは、実行時に次の条件をチェックされます。 これらの条件のいずれかが見つからなかった場合、マネージド コードの実行が失敗し、例外がスローされます。  
  
### <a name="unsafe"></a>UNSAFE  
 アセンブリを明示的に読み込む場合は、バイト配列から**System.Reflection.Assembly.Load()** メソッドを呼び出すか **、Reflection.Emit**名前空間を使用して暗黙的に読み込むのは許可されていません。  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 **UNSAFE**条件はすべてチェックされます。  
  
 サポートされているアセンブリの一覧の中で、次のホスト保護属性 (HPA) 値で注釈を付けられている型およびメンバーはすべて許可されません。  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 HPA の詳細と、サポートされているアセンブリで許可されない型とメンバーの一覧については、「[ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)」を参照してください。  
  
### <a name="safe"></a>SAFE  
 すべての**EXTERNAL_ACCESS**条件がチェックされます。  
  
## <a name="see-also"></a>参照  
 [サポートされている .NET フレームワーク ライブラリ](../../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md)   
 [CLR 統合コード アクセス セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [アセンブリの作成](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  
