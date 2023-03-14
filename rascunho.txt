import React from 'react';
import { 
  StyleSheet,
  Button,
  View,
  SafeAreaView,
  Text,
  Image,
} from 'react-native';
import * as WebBrowser from 'expo-web-browser';

const Separator = () => <View style={styles.separator} />;

export default function ChatScreen() {
  const openChat = async () => {
    const result = await WebBrowser.openAuthSessionAsync(
      'https://chat.openai.com',
      'https://chat.openai.com/oauth_callback'
    );

    console.log(result);
  }

  return (
    <SafeAreaView style={styles.container}>
       <View>
       <Image
            source={require('./assets/favicon.png')}
            style={styles.buttonImageIconStyle}
            
          />
       <Text  style={styles.title}>
          Welcome to ChatGPT
       </Text>
       <Separator />
       <View>
          <Button style={styles.button}
           onPress={openChat} 
           color='#19c37d'
           title="Abrir Chat" 
          />
       </View>
      </View>
     
    </SafeAreaView>
  );
}


const styles = StyleSheet.create({

  container:{
    backgroundColor: '#2d3748', 
    flex: 1, 
    justifyContent: 'center', 
    alignItems: 'center'
    
   },
   title: {
    textAlign: 'center',
    marginVertical: 8,
    color: '#FFFFFF',
    fontSize: 20,
  },
  
  separator: {
    marginVertical: 10,
    borderBottomColor: '#2d3748',
    borderBottomWidth: StyleSheet.hairlineWidth,
  },
  button:{
    padding: 20,
    margin: 4,
    borderRadius: 50,
    backgroundColor: '#363636',
    color: '#fff',
    borderColor: '#777',
    textAlign: 'center',
    
  },
  buttonImageIconStyle: {
    alignItems: 'center',
    marginLeft: 58,
    justifyContent: 'center', 
    resizeMode: 'stretch',
  },
});
