def generar_gif_y_guardar():
    numero = '{:02d}'.format(random.randint(0, 99))  # Genera un número aleatorio entre 00 y 99
    
    # Configuración de tamaño de imagen
    width, height = 200, 200
    
    # Función para generar el cuadro con el número
    def generate_frame():
        img = Image.new('RGB', (width, height), color='white')
        draw = ImageDraw.Draw(img)
        draw.text((width // 2, height // 2), numero, fill='black')
        return img

    # Generar los cuadros y guardarlos como GIF
    frames = []
    for _ in range(10):  # Número de cuadros en el GIF
        frame = generate_frame()
        frames.append(frame)

    # Guardar el GIF en el directorio actual
    ruta_actual = os.getcwd()
    gif_path = os.path.join(ruta_actual, 'random_number.gif')
    
    try:
        frames[0].save(gif_path, save_all=True, append_images=frames[1:], duration=500, loop=0) # Duración en milisegundos (0.5 segundos)
        print(f"Se ha guardado el GIF en: {gif_path}")
    except Exception as e:
        print(f"Error al guardar el GIF: {e}")

    return gif_path
