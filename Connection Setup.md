## Objectives:
1. Pagkatapos nito maari mo ng maconnect ang Supabase at Flutter project mo

## Paano i connect ang Flutter application sa Supabase Project

1. Pindotin ang "Connect"
2. Pumunta sa "Mobile Frameworks"
3. Piliin ang "Flutter" sa Framework
4. Gumawa ng Flutter Application
5. I-modify ang "main.dart" file

   ```dart
   ....
   import 'package:supabase_flutter/supabase_flutter.dart';
   
     Future<void> main() async {
        await Supabase.initialize(
           url: 'YOUR_URL',
           anonKey: 'YOUR_ANON_KEY',
      );
      runApp(MyApp());
    }
   ....
   ```
