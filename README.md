import discord
import random
import asyncio

# Crea una clase para el bot
class BensonBot(discord.Client):
    def __init__(self):
        super().__init__()
        self.responses = [
            "¿No lo sabes? Ya estás atrapado aquí.",
            "Yo siempre te estoy observando, ¿lo sabías?",
            "No sé por qué me sigues, pero sigues aquí...",
            "El tiempo no existe. Estás soñando.",
            "¿Es este un sueño o todo es real? ¿Sabes la diferencia?",
            "Es demasiado tarde para huir...",
            "¿Sabes qué va a pasar ahora?",
            "¿Qué harías si todo esto desapareciera?"
        ]
        
    async def on_ready(self):
        print(f'{self.user} ha iniciado sesión en Discord.')
        
    async def on_message(self, message):
        if message.author == self.user:  # Ignora los mensajes del propio bot
            return
        
        # Responde solo si el mensaje contiene ciertas palabras
        if "benson" in message.content.lower() or "regular show" in message.content.lower():
            await message.channel.send(self.get_random_response())

        # Responde en caso de comandos especiales, como "help"
        elif message.content.lower() == "!help":
            await message.channel.send("Puedo decirte cosas perturbadoras o simplemente quedarme en silencio... depende de ti.")

    def get_random_response(self):
        return random.choice(self.responses)

# Crea una instancia del bot
intents = discord.Intents.default()
intents.message_content = True  # Asegúrate de que el bot pueda leer el contenido de los mensajes
client = BensonBot()

# Inicia el bot con su token
token = 'TU_TOKEN_DE_DISCORD_AQUI'  # Asegúrate de poner aquí el token de tu bot
client.run(token)![download](https://github.com/user-attachments/assets/cc7fedb3-4e04-48b1-b00f-00cc64ac97b7)
