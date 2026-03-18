- 👋 Hi, I’m @ImEneko123
- 👀 I’m interested in creating an AI
- 🌱 I’m currently learning in school
- 💞️ I’m looking to collaborate on projects like doing videogames
- 📫 How to reach me by enekogarciaf@gmail.com
- 😄 Pronouns: Potato brain
- ⚡ Fun fact: I like videogames

<!---
ImEneko123/ImEneko123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import { loadModel, predict } from './model.js';
import * as ort from 'onnxruntime-web';

async function main() {
  const session = await loadModel();

  // Crear un tensor vacío de 28x28
  const data = new Float32Array(28 * 28).fill(0);
  const tensor = new ort.Tensor("float32", data, [1, 1, 28, 28]);

  const output = await predict(tensor);

  console.log("Resultado:", output);

  // Mostrar el resultado en pantalla
  const pre = document.createElement("pre");
  pre.textContent = "Resultado del modelo:\n" + JSON.stringify(output, null, 2);
  document.body.appendChild(pre);
}

main();
